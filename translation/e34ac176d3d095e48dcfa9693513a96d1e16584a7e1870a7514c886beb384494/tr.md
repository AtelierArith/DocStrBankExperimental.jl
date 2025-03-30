# Multi-processing and Distributed Computing

Bir dağıtık bellek paralel hesaplama uygulaması, Julia ile birlikte gönderilen standart kütüphanenin bir parçası olarak [`Distributed`](@ref man-distributed) modülü tarafından sağlanmaktadır.

Çoğu modern bilgisayar birden fazla CPU'ya sahiptir ve birkaç bilgisayar bir küme halinde bir araya getirilebilir. Bu birden fazla CPU'nun gücünden yararlanmak, birçok hesaplamanın daha hızlı tamamlanmasını sağlar. Performansı etkileyen iki ana faktör vardır: CPU'ların kendilerinin hızı ve belleğe erişim hızları. Bir kümede, belirli bir CPU'nun aynı bilgisayardaki (düğüm) RAM'e en hızlı erişime sahip olacağı oldukça açıktır. Belki de daha şaşırtıcı olan, ana belleğin hızı ile [cache](https://www.akkadia.org/drepper/cpumemory.pdf) arasındaki farklılıklar nedeniyle tipik bir çok çekirdekli dizüstü bilgisayarda benzer sorunların geçerli olmasıdır. Sonuç olarak, iyi bir çoklu işlem ortamı, belirli bir CPU tarafından bir bellek parçasının "sahipliği" üzerinde kontrol sağlamalıdır. Julia, programların birden fazla süreçte ayrı bellek alanlarında aynı anda çalışmasına izin vermek için mesaj geçişine dayalı bir çoklu işlem ortamı sağlar.

Julia'nın mesaj iletim uygulaması, MPI gibi diğer ortamlardan farklıdır[^1]. Julia'daki iletişim genellikle "tek taraflıdır", bu da programcının iki işlemli bir operasyonda yalnızca bir işlemi açıkça yönetmesi gerektiği anlamına gelir. Ayrıca, bu işlemler genellikle "mesaj gönder" ve "mesaj al" gibi görünmek yerine, kullanıcı fonksiyonlarına yapılan çağrılar gibi daha yüksek seviyeli işlemlere benzer.

Dağıtık programlama Julia'da iki temel ilkeye dayanır: *uzak referanslar* ve *uzak çağrılar*. Uzak bir referans, herhangi bir işlemden belirli bir işlemde depolanan bir nesneye atıfta bulunmak için kullanılabilen bir nesnedir. Uzak bir çağrı, bir işlemin başka (muhtemelen aynı) bir işlemde belirli bir işlevi belirli argümanlarla çağırma talebidir.

Uzaktan referanslar iki çeşitte gelir: [`Future`](@ref Distributed.Future) ve [`RemoteChannel`](@ref).

Uzak bir çağrı, sonucuna [`Future`](@ref Distributed.Future) döner. Uzak çağrılar hemen döner; çağrıyı yapan süreç, çağrı başka bir yerde gerçekleşirken bir sonraki işlemini sürdürür. Bir uzak çağrının bitmesini beklemek için dönen [`wait`](@ref) üzerinde [`fetch`](@ref) çağrısını yaparak sonucun tam değerini elde edebilirsiniz.

Diğer yandan, [`RemoteChannel`](@ref) ler yeniden yazılabilir. Örneğin, birden fazla işlem, aynı uzak `Channel`'ı referans alarak işleme koordinasyonu yapabilir.

Her işlemle ilişkili bir tanımlayıcı vardır. Etkileşimli Julia istemcisini sağlayan işlem her zaman `id` değeri 1 olan bir işlemdir. Varsayılan olarak paralel işlemler için kullanılan işlemler "işçiler" olarak adlandırılır. Sadece bir işlem olduğunda, işlem 1 bir işçi olarak kabul edilir. Aksi takdirde, işçiler işlem 1 dışındaki tüm işlemler olarak kabul edilir. Sonuç olarak, [`pmap`](@ref) gibi paralel işleme yöntemlerinden fayda sağlamak için 2 veya daha fazla işlem eklemek gereklidir. Tek bir işlem eklemek, uzun bir hesaplama işçi üzerinde çalışırken ana işlemde başka şeyler yapmak istiyorsanız faydalıdır.

`julia -p n` komutu, yerel makinede `n` işçi süreci sağlar. Genel olarak, `n`'nin makinedeki CPU iş parçacığı (mantıksal çekirdek) sayısına eşit olması mantıklıdır. `-p` argümanının, [`Distributed`](@ref man-distributed) modülünü örtük olarak yüklediğini unutmayın.

```julia
$ julia -p 2

julia> r = remotecall(rand, 2, 2, 2)
Future(2, 1, 4, nothing)

julia> s = @spawnat 2 1 .+ fetch(r)
Future(2, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.18526  1.50912
 1.16296  1.60607
```

[`remotecall`](@ref) çağrılacak fonksiyondur. Julia'daki çoğu paralel programlama, belirli süreçlere veya mevcut süreç sayısına atıfta bulunmaz, ancak `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` daha ince kontrol sağlayan düşük seviyeli bir arayüz olarak kabul edilir. `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566`'ya ilk argüman, işi yapacak sürecin `id`'sidir ve kalan argümanlar çağrılan fonksiyona iletilecektir.

Gördüğünüz gibi, ilk satırda işlem 2'den 2'ye 2 boyutlu rastgele bir matris oluşturmasını istedik ve ikinci satırda ona 1 eklemesini istedik. Her iki hesaplamanın sonucu `r` ve `s` adlı iki gelecekte mevcuttur. [`@spawnat`](@ref) makrosu, ilk argümanla belirtilen işlemde ikinci argümandaki ifadeyi değerlendirir.

Bazen uzaktan hesaplanan bir değeri hemen almak isteyebilirsiniz. Bu genellikle, bir sonraki yerel işlem için gerekli verileri elde etmek amacıyla uzaktan bir nesneden okuma yaptığınızda olur. Bu amaçla [`remotecall_fetch`](@ref) fonksiyonu mevcuttur. Bu, `fetch(remotecall(...))` ile eşdeğerdir ancak daha verimlidir.

```julia-repl
julia> remotecall_fetch(r-> fetch(r)[1, 1], 2, r)
0.18526337335308085
```

Bu, işçi 2'deki diziyi alır ve ilk değeri döndürür. Not: `fetch` bu durumda herhangi bir veri taşımadığı için, dizinin sahibi olan işçi üzerinde çalıştırılır. Ayrıca şunları da yazabilirsiniz:

```julia-repl
julia> remotecall_fetch(getindex, 2, r, 1, 1)
0.10824216411304866
```

[`getindex(r,1,1)`](@ref) [equivalent](@ref man-array-indexing) `r[1,1]` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `r` `

İşleri kolaylaştırmak için `:any` sembolü [`@spawnat`](@ref)'ya geçirilebilir; bu, işlemin nerede yapılacağını sizin için seçer:

```julia-repl
julia> r = @spawnat :any rand(2,2)
Future(2, 1, 4, nothing)

julia> s = @spawnat :any 1 .+ fetch(r)
Future(3, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.38854  1.9098
 1.20939  1.57158
```

Not edin ki `1 .+ fetch(r)` yerine `1 .+ r` kullandık. Bunun nedeni, kodun nerede çalışacağını bilmememizdir, bu nedenle genel olarak [`fetch`](@ref)'nın `r`'yi toplama işlemini yapan işleme taşımak için gerekli olabileceğidir. Bu durumda, [`@spawnat`](@ref) `r`'yi sahip olduğu işlemde hesaplamayı gerçekleştirecek kadar akıllıdır, bu nedenle `4d61726b646f776e2e436f64652822222c202266657463682229_40726566` bir no-op (hiçbir iş yapılmaz) olacaktır.

(Bu [`@spawnat`](@ref) yerleşik değildir, ancak Julia'da [macro](@ref man-macros) olarak tanımlanmıştır. Kendi böyle yapılarınızı tanımlamanız mümkündür.)

Önemli bir şey, bir [`Future`](@ref Distributed.Future) alındıktan sonra, değerinin yerel olarak önbelleğe alınacağıdır. Daha fazla [`fetch`](@ref) çağrısı bir ağ geçişi gerektirmez. Tüm referans alan `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` alındıktan sonra, uzaktaki saklanan değer silinir.

[`@async`](@ref) [`@spawnat`](@ref) yerel süreçte görevleri çalıştırır. Her süreç için bir "besleyici" görevi oluşturmak için kullanıyoruz. Her görev, hesaplanması gereken bir sonraki indeksi alır, ardından sürecinin bitmesini bekler, sonra da indeksler tükenene kadar tekrar eder. Besleyici görevlerin, ana görev [`@sync`](@ref) bloğunun sonuna ulaşana kadar çalışmaya başlamadığını unutmayın; bu noktada kontrolü bırakır ve tüm yerel görevlerin tamamlanmasını bekler. v0.7 ve sonrasında, besleyici görevler `nextidx` aracılığıyla durumu paylaşabilir çünkü hepsi aynı süreçte çalışır. `Tasks` işbirlikçi olarak planlansa bile, bazı bağlamlarda kilitleme gerekebilir, örneğin [asynchronous I/O](@ref faq-async-io) gibi. Bu, bağlam değişikliklerinin yalnızca iyi tanımlanmış noktalarda gerçekleştiği anlamına gelir: bu durumda, [`remotecall_fetch`](@ref) çağrıldığında. Bu, mevcut uygulama durumudur ve gelecekteki Julia sürümleri için değişebilir; çünkü N `Tasks`'ı M `Process` üzerinde çalıştırmayı mümkün kılmak amacıyla tasarlanmıştır, yani [M:N Threading](https://en.wikipedia.org/wiki/Thread_(computing)#Models). O zaman `nextidx` için bir kilit alma/verme modeli gerekecektir, çünkü birden fazla sürecin aynı anda bir kaynağı okuma-yazma yapmasına izin vermek güvenli değildir.

## [Code Availability and Loading Packages](@id code-availability)

Kodunuz, onu çalıştıran herhangi bir süreçte mevcut olmalıdır. Örneğin, aşağıdakini Julia istemine yazın:

```julia-repl
julia> function rand2(dims...)
           return 2*rand(dims...)
       end

julia> rand2(2,2)
2×2 Array{Float64,2}:
 0.153756  0.368514
 1.15119   0.918912

julia> fetch(@spawnat :any rand2(2,2))
ERROR: RemoteException(2, CapturedException(UndefVarError(Symbol("#rand2"))))
Stacktrace:
[...]
```

Process 1, `rand2` fonksiyonunu biliyordu, ancak işlem 2 bilmiyordu.

En yaygın olarak, kodu dosyalardan veya paketlerden yükleyeceksiniz ve hangi süreçlerin kodu yükleyeceğini kontrol etme konusunda önemli bir esnekliğe sahipsiniz. Aşağıdaki kodu içeren bir dosya, `DummyModule.jl`'yi düşünün:

```julia
module DummyModule

export MyType, f

mutable struct MyType
    a::Int
end

f(x) = x^2+1

println("loaded")

end
```

`MyType`'ı tüm süreçlerde referans almak için, `DummyModule.jl` her süreçte yüklenmelidir. `include("DummyModule.jl")` çağrısı yalnızca tek bir süreçte yükler. Her süreçte yüklemek için, [`@everywhere`](@ref) makrosunu kullanın (Julia'yı `julia -p 2` ile başlatın):

```julia-repl
julia> @everywhere include("DummyModule.jl")
loaded
      From worker 3:    loaded
      From worker 2:    loaded
```

Her zamanki gibi, bu `DummyModule`'ü herhangi bir süreçte kapsam içine almaz, bu da [`using`](@ref) veya [`import`](@ref) gerektirir. Dahası, `DummyModule` bir süreçte kapsam içine alındığında, diğer hiçbir süreçte kapsamda değildir:

```julia-repl
julia> using .DummyModule

julia> MyType(7)
MyType(7)

julia> fetch(@spawnat 2 MyType(7))
ERROR: On worker 2:
UndefVarError: `MyType` not defined in `Main`
⋮

julia> fetch(@spawnat 2 DummyModule.MyType(7))
MyType(7)
```

Ancak, `DummyModule`'u yüklemiş bir işleme `MyType` göndermek hala mümkündür, hatta bu tür kapsamda olmasa bile:

```julia-repl
julia> put!(RemoteChannel(2), MyType(7))
RemoteChannel{Channel{Any}}(2, 1, 13)
```

Bir dosya, başlangıçta birden fazla işlemde `-L` bayrağı ile önceden yüklenebilir ve bir sürücü betiği hesaplamayı yönlendirmek için kullanılabilir:

```
julia -p <n> -L file1.jl -L file2.jl driver.jl
```

Yukarıdaki örnekteki sürücü betiğini çalıştıran Julia sürecinin bir `id`'si 1'dir, tıpkı etkileşimli bir istemci sağlayan bir sürecin `id`'si gibi.

Son olarak, eğer `DummyModule.jl` bağımsız bir dosya değil de bir paket ise, o zaman `using DummyModule` tüm süreçlerde `DummyModule.jl`'yi *yükleyecek*, ancak yalnızca [`using`](@ref) çağrıldığında o süreçte kapsam içine alacaktır.

## Starting and managing worker processes

Temel Julia kurulumu, iki tür küme için yerleşik destek sunar:

  * `-p` seçeneği ile belirtilen yerel küme yukarıda gösterildiği gibi.
  * Bir `--machine-file` seçeneği kullanarak makineleri kapsayan bir küme. Bu, belirtilen makinelerde Julia işçi süreçlerini başlatmak için parolasız bir `ssh` girişi kullanır (mevcut ana bilgisayar ile aynı yoldan). Her makine tanımı `[count*][user@]host[:port] [bind_addr[:port]]` biçimindedir. `user`, mevcut kullanıcıya, `port` ise standart ssh portuna varsayılan olarak ayarlanır. `count`, düğümde başlatılacak işçi sayısını belirtir ve varsayılan olarak 1'dir. İsteğe bağlı `bind-to bind_addr[:port]`, diğer işçilerin bu işçiye bağlanmak için kullanması gereken IP adresini ve portu belirtir.

!!! note
    Julia genellikle geriye dönük uyumluluğa özen gösterse de, kodun işçi süreçlere dağıtımı [`Serialization.serialize`](@ref)'ya dayanır. İlgili belgede belirtildiği gibi, bu durum farklı Julia sürümleri arasında çalışacağının garantisi yoktur, bu nedenle tüm makinelerdeki tüm işçilerin aynı sürümü kullanması önerilir.


Fonksiyonlar [`addprocs`](@ref), [`rmprocs`](@ref), [`workers`](@ref) ve diğerleri, bir kümedeki süreçleri eklemek, kaldırmak ve sorgulamak için programatik bir araç olarak mevcuttur.

```julia-repl
julia> using Distributed

julia> addprocs(2)
2-element Array{Int64,1}:
 2
 3
```

Modül [`Distributed`](@ref man-distributed), [`addprocs`](@ref) çağrılmadan önce ana süreçte açıkça yüklenmelidir. İşçi süreçlerde otomatik olarak kullanılabilir hale getirilir.

!!! note
    Not edin ki, işçiler `~/.julia/config/startup.jl` başlangıç betiğini çalıştırmazlar ve global durumlarını (komut satırı anahtarları, global değişkenler, yeni yöntem tanımları ve yüklenmiş modüller gibi) diğer çalışan süreçlerle senkronize etmezler. Belirli bir ortamla bir işçiyi başlatmak için `addprocs(exeflags="--project")` kullanabilir ve ardından `@everywhere using <modulename>` veya `@everywhere include("file.jl")` komutlarını kullanabilirsiniz.


Diğer küme türleri, aşağıda [ClusterManagers](@ref) bölümünde açıklandığı gibi kendi özel `ClusterManager`'ınızı yazarak desteklenebilir.

## Data Movement

Mesaj göndermek ve veri taşımak, dağıtık bir programdaki en büyük yükü oluşturur. Gönderilen mesaj sayısını ve veri miktarını azaltmak, performans ve ölçeklenebilirlik elde etmek için kritik öneme sahiptir. Bu amaçla, Julia'nın çeşitli dağıtık programlama yapıları tarafından gerçekleştirilen veri hareketini anlamak önemlidir.

[`fetch`](@ref) açık bir veri hareketi işlemi olarak kabul edilebilir, çünkü doğrudan bir nesnenin yerel makineye taşınmasını talep eder. [`@spawnat`](@ref) (ve birkaç ilgili yapı) de veri taşır, ancak bu o kadar belirgin değildir, bu nedenle dolaylı bir veri hareketi işlemi olarak adlandırılabilir. Rastgele bir matris oluşturma ve kare alma konusundaki bu iki yaklaşımı düşünün:

Yöntem 1:

```julia-repl
julia> A = rand(1000,1000);

julia> Bref = @spawnat :any A^2;

[...]

julia> fetch(Bref);
```

Yöntem 2:

```julia-repl
julia> Bref = @spawnat :any rand(1000,1000)^2;

[...]

julia> fetch(Bref);
```

Fark, önemsiz görünüyor, ancak aslında [`@spawnat`](@ref) davranışı nedeniyle oldukça önemlidir. İlk yöntemde, rastgele bir matris yerel olarak oluşturulur, ardından karesini almak için başka bir işleme gönderilir. İkinci yöntemde, rastgele bir matris hem başka bir işlemde oluşturulur hem de karesi alınır. Bu nedenle, ikinci yöntem ilkine göre çok daha az veri gönderir.

Bu oyuncak örnekte, iki yöntem kolayca ayırt edilebilir ve seçilebilir. Ancak, gerçek bir programda veri hareketini tasarlamak daha fazla düşünce ve muhtemelen bazı ölçümler gerektirebilir. Örneğin, eğer birinci işlem matris `A`'ya ihtiyaç duyuyorsa, o zaman birinci yöntem daha iyi olabilir. Ya da, eğer `A`'yı hesaplamak pahalıysa ve yalnızca mevcut işlemde varsa, o zaman başka bir işleme taşımak kaçınılmaz olabilir. Ya da, mevcut işlemin [`@spawnat`](@ref) ile `fetch(Bref)` arasında yapacak çok az işi varsa, o zaman paralelliği tamamen ortadan kaldırmak daha iyi olabilir. Ya da `rand(1000,1000)` daha pahalı bir işlemle değiştirilirse, o zaman bu adım için başka bir `4d61726b646f776e2e436f64652822222c202240737061776e61742229_40726566` ifadesi eklemek mantıklı olabilir.

## Global variables

Uzakta yürütülen ifadeler [`@spawnat`](@ref) aracılığıyla veya uzaktan yürütme için belirtilen kapamalar [`remotecall`](@ref) global değişkenlere atıfta bulunabilir. `Main` modülündeki global bağlamalar, diğer modüllerdeki global bağlamalardan biraz farklı şekilde ele alınır. Aşağıdaki kod parçasını düşünün:

```julia-repl
A = rand(10,10)
remotecall_fetch(()->sum(A), 2)
```

Bu durumda [`sum`](@ref) uzak süreçte tanımlanmalıdır. `A`'nın yerel çalışma alanında tanımlı bir global değişken olduğunu unutmayın. İşçi 2'nin `Main` altında `A` adında bir değişkeni yoktur. `()->sum(A)` kapanışını işçi 2'ye göndermek, `Main.A`'nın 2'de tanımlanmasına neden olur. `Main.A`, [`remotecall_fetch`](@ref) çağrısı döndükten sonra bile işçi 2'de var olmaya devam eder. Gömülü global referanslarla yapılan uzak çağrılar (yalnızca `Main` modülü altında) global değişkenleri şu şekilde yönetir:

  * Yeni küresel bağlamlar, bir uzak çağrının parçası olarak referans alındıklarında hedef işçilerde oluşturulur.
  * Küresel sabitler, uzak düğümlerde de sabitler olarak tanımlanır.
  * Küresel değişkenler, yalnızca bir uzak çağrı bağlamında bir hedef işçiye yeniden gönderilir ve yalnızca değeri değiştiyse. Ayrıca, küme, düğümler arasında küresel bağlamaları senkronize etmez. Örneğin:

    ```julia
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 2) # worker 2
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 3) # worker 3
    A = nothing
    ```

    Yukarıdaki kod parçasını çalıştırmak, işçi 2'de `Main.A`'nın değerinin işçi 3'teki `Main.A`'dan farklı olmasına neden olurken, düğüm 1'de `Main.A`'nın değeri `nothing` olarak ayarlanmıştır.

Görmüş olabileceğiniz gibi, küresel değişkenlerle ilişkili bellek, ana makinede yeniden atandıklarında toplanabilir, ancak işçilerde böyle bir işlem yapılmaz çünkü bağlamalar geçerliliğini korur. [`clear!`](@ref) artık gerekli olmadıklarında uzak düğümlerde belirli küresel değişkenleri `nothing` olarak manuel olarak yeniden atamak için kullanılabilir. Bu, düzenli bir çöp toplama döngüsü kapsamında onlarla ilişkili herhangi bir belleği serbest bırakacaktır.

Bu nedenle, programlar uzaktan çağrılarda global değişkenlere atıfta bulunurken dikkatli olmalıdır. Aslında, mümkünse bunlardan tamamen kaçınmak tercih edilir. Eğer global değişkenlere atıfta bulunmanız gerekiyorsa, global değişkenleri yerelleştirmek için `let` blokları kullanmayı düşünün.

Örneğin:

```julia-repl
julia> A = rand(10,10);

julia> remotecall_fetch(()->A, 2);

julia> B = rand(10,10);

julia> let B = B
           remotecall_fetch(()->B, 2)
       end;

julia> @fetchfrom 2 InteractiveUtils.varinfo()
name           size summary
––––––––– ––––––––– ––––––––––––––––––––––
A         800 bytes 10×10 Array{Float64,2}
Base                Module
Core                Module
Main                Module
```

Görüldüğü gibi, global değişken `A` işçi 2'de tanımlanmıştır, ancak `B` yerel bir değişken olarak yakalanmıştır ve bu nedenle işçi 2'de `B` için bir bağlama mevcut değildir.

## Parallel Map and Loops

Şans eseri, birçok yararlı paralel hesaplama veri hareketi gerektirmez. Yaygın bir örnek, birden fazla işlemin bağımsız simülasyon denemelerini aynı anda işleyebileceği Monte Carlo simülasyonudur. İki işlemde madeni paraları çevirmek için [`@spawnat`](@ref) kullanabiliriz. Öncelikle, aşağıdaki işlevi `count_heads.jl` dosyasına yazın:

```julia
function count_heads(n)
    c::Int = 0
    for i = 1:n
        c += rand(Bool)
    end
    c
end
```

`count_heads` fonksiyonu, `n` rastgele biti toplar. İşte iki makinede bazı denemeler yapmanın ve sonuçları bir araya getirmenin yolu:

```julia-repl
julia> @everywhere include_string(Main, $(read("count_heads.jl", String)), "count_heads.jl")

julia> a = @spawnat :any count_heads(100000000)
Future(2, 1, 6, nothing)

julia> b = @spawnat :any count_heads(100000000)
Future(3, 1, 7, nothing)

julia> fetch(a)+fetch(b)
100001564
```

Bu örnek, güçlü ve sıkça kullanılan bir paralel programlama desenini göstermektedir. Birçok iterasyon, birkaç işlem üzerinde bağımsız olarak çalışır ve ardından sonuçları bir fonksiyon kullanarak birleştirilir. Birleştirme sürecine *reduction* denir, çünkü genellikle tensör-rank azaltıcıdır: bir sayı vektörü tek bir sayıya, ya da bir matris tek bir satıra veya sütuna indirgenir, vb. Kodda, bu genellikle `x = f(x,v[i])` deseni gibi görünür; burada `x` toplayıcıdır, `f` azaltma fonksiyonudur ve `v[i]` azaltılan elemanlardır. `f`'nin birleşimsel olması arzu edilir, böylece işlemlerin hangi sırayla yapıldığı önemli değildir.

Bu desenin `count_heads` ile kullanımının genelleştirilebileceğini unutmayın. İki açık [`@spawnat`](@ref) ifadesi kullandık, bu da paralelliği iki işlemle sınırlıyor. Herhangi bir işlem sayısında çalışmak için, dağıtılmış bellek içinde çalışan bir *paralel for döngüsü* kullanabiliriz; bu, Julia'da [`@distributed`](@ref) şeklinde yazılabilir:

```julia
nheads = @distributed (+) for i = 1:200000000
    Int(rand(Bool))
end
```

Bu yapı, yinelemeleri birden fazla işleme atama ve bunları belirli bir azaltma ile birleştirme desenini uygular (bu durumda `(+)`). Her yinelemenin sonucu, döngü içindeki son ifadenin değeri olarak alınır. Tüm paralel döngü ifadesi kendisi nihai sonuca değer.

Paralel for döngülerinin seri for döngülerine benzer göründüğüne dikkat edin, ancak davranışları dramatik şekilde farklıdır. Özellikle, yinelemeler belirli bir sırada gerçekleşmez ve değişkenlere veya dizilere yapılan yazmalar küresel olarak görünür olmayacaktır, çünkü yinelemeler farklı süreçlerde çalışır. Paralel döngü içinde kullanılan herhangi bir değişken, her bir işleme kopyalanacak ve yayınlanacaktır.

Örneğin, aşağıdaki kod istenildiği gibi çalışmayacaktır:

```julia
a = zeros(100000)
@distributed for i = 1:100000
    a[i] = i
end
```

Bu kod, `a`'nın tamamını başlatmayacaktır, çünkü her işlem onun ayrı bir kopyasına sahip olacaktır. Bu tür paralel for döngülerinden kaçınılmalıdır. Neyse ki, [Shared Arrays](@ref man-shared-arrays) bu sınırlamanın üstesinden gelmek için kullanılabilir:

```julia
using SharedArrays

a = SharedArray{Float64}(10)
@distributed for i = 1:10
    a[i] = i
end
```

Dışarıdaki değişkenleri paralel döngülerde kullanmak, eğer değişkenler yalnızca okunuyorsa, tamamen makuldür:

```julia
a = randn(1000)
@distributed (+) for i = 1:100000
    f(a[rand(1:end)])
end
```

Burada her yineleme, tüm süreçler tarafından paylaşılan bir `a` vektöründen rastgele seçilen bir örneğe `f` uygulamaktadır.

Gördüğünüz gibi, azaltma operatörü gerekli değilse atlanabilir. Bu durumda, döngü asenkron olarak çalışır, yani mevcut tüm işçilerde bağımsız görevler başlatır ve tamamlanmayı beklemeden hemen [`Future`](@ref Distributed.Future) dizisini döndürür. Çağrıcı, daha sonra `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` tamamlanmalarını [`fetch`](@ref) çağrısı ile bekleyebilir veya döngünün sonunda [`@sync`](@ref) ile ön ekleyerek tamamlanmayı bekleyebilir, örneğin `@sync @distributed for`.

Bazı durumlarda bir azaltma operatörüne ihtiyaç yoktur ve yalnızca bir aralıktaki (veya daha genel olarak, bir koleksiyondaki tüm öğelere) bir fonksiyon uygulamak isteriz. Bu, Julia'da [`pmap`](@ref) fonksiyonu olarak uygulanan başka bir yararlı işlemdir. Örneğin, birkaç büyük rastgele matrisin tekil değerlerini paralel olarak aşağıdaki gibi hesaplayabiliriz:

```julia-repl
julia> M = Matrix{Float64}[rand(1000,1000) for i = 1:10];

julia> pmap(svdvals, M);
```

Julia'nın [`pmap`](@ref) her fonksiyon çağrısının büyük miktarda iş yaptığı durumlar için tasarlanmıştır. Buna karşılık, `@distributed for` her iterasyonun küçük olduğu, belki de sadece iki sayıyı toplamakla sınırlı olduğu durumları yönetebilir. Hem `4d61726b646f776e2e436f64652822222c2022706d61702229_40726566` hem de `@distributed for` paralel hesaplama için yalnızca işçi süreçlerini kullanır. `@distributed for` durumunda, nihai azaltma çağıran süreçte yapılır.

## Remote References and AbstractChannels

Uzak referanslar her zaman bir `AbstractChannel` uygulamasına atıfta bulunur.

Bir `AbstractChannel` (örneğin `Channel`) için somut bir uygulama, [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) ve [`wait`](@ref) uygulamak zorundadır. Bir [`Future`](@ref Distributed.Future) tarafından atıfta bulunulan uzak nesne, `Channel{Any}(1)` içinde saklanmaktadır, yani `Any` türündeki nesneleri tutabilen boyutu 1 olan bir `Channel`.

[`RemoteChannel`](@ref), yeniden yazılabilir, her türlü ve boyuttaki kanallara veya başka bir `AbstractChannel` uygulamasına işaret edebilir.

`RemoteChannel(f::Function, pid)()` yapıcısı, belirli bir türde birden fazla değeri tutan kanallara referanslar oluşturmamıza olanak tanır. `f`, `pid` üzerinde yürütülen bir işlevdir ve bir `AbstractChannel` döndürmelidir.

Örneğin, `RemoteChannel(()->Channel{Int}(10), pid)`, `Int` türünde ve 10 boyutunda bir kanala referans döndürecektir. Kanal, işçi `pid` üzerinde bulunmaktadır.

Yöntemler [`put!`](@ref), [`take!`](@ref), [`fetch`](@ref), [`isready`](@ref) ve [`wait`](@ref) bir [`RemoteChannel`](@ref) üzerinde arka planda depolama alanına yönlendirilmiştir.

[`RemoteChannel`](@ref) bu nedenle kullanıcı tarafından uygulanan `AbstractChannel` nesnelerine atıfta bulunmak için kullanılabilir. Bunun basit bir örneği, bir sözlüğü uzak depolama alanı olarak kullanan aşağıdaki `DictChannel`'dır:

```jldoctest
julia> struct DictChannel{T} <: AbstractChannel{T}
           d::Dict
           cond_take::Threads.Condition    # waiting for data to become available
           DictChannel{T}() where {T} = new(Dict(), Threads.Condition())
           DictChannel() = DictChannel{Any}()
       end

julia> begin
       function Base.put!(D::DictChannel, k, v)
           @lock D.cond_take begin
               D.d[k] = v
               notify(D.cond_take)
           end
           return D
       end
       function Base.take!(D::DictChannel, k)
           @lock D.cond_take begin
               v = fetch(D, k)
               delete!(D.d, k)
               return v
           end
       end
       Base.isready(D::DictChannel) = @lock D.cond_take !isempty(D.d)
       Base.isready(D::DictChannel, k) = @lock D.cond_take haskey(D.d, k)
       function Base.fetch(D::DictChannel, k)
           @lock D.cond_take begin
               wait(D, k)
               return D.d[k]
           end
       end
       function Base.wait(D::DictChannel, k)
           @lock D.cond_take begin
               while !isready(D, k)
                   wait(D.cond_take)
               end
           end
       end
       end;

julia> d = DictChannel();

julia> isready(d)
false

julia> put!(d, :k, :v);

julia> isready(d, :k)
true

julia> fetch(d, :k)
:v

julia> wait(d, :k)

julia> take!(d, :k)
:v

julia> isready(d, :k)
false
```

## Channels and RemoteChannels

  * Bir [`Channel`](@ref) bir süreçle sınırlıdır. İşçi 2, işçi 3'teki bir `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`'ya doğrudan atıfta bulunamaz ve tersine. Ancak, bir [`RemoteChannel`](@ref), işçiler arasında değerler koyabilir ve alabilir.
  * Bir [`RemoteChannel`](@ref), [`Channel`](@ref) için bir *tutacak* olarak düşünülebilir.
  * `pid` ile ilişkilendirilen işlem kimliği, [`RemoteChannel`](@ref), yedek depolamanın, yani yedek [`Channel`](@ref) bulunduğu işlemi tanımlar.
  * Herhangi bir [`RemoteChannel`](@ref) referansı olan işlem, kanaldan öğeleri alabilir ve bırakabilir. Veriler, bir `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` ile ilişkilendirilmiş işleme otomatik olarak gönderilir (veya o işlemden alınır).
  * [`Channel`](@ref) bir `serileştirme` işlemi, kanalda bulunan herhangi bir veriyi de serileştirir. Bu nedenle, `deserileştirme` işlemi aslında orijinal nesnenin bir kopyasını oluşturur.
  * Diğer yandan, [`RemoteChannel`](@ref) nesnesinin serileştirilmesi, yalnızca bir tanımlayıcının serileştirilmesini içerir; bu tanımlayıcı, tutamaç tarafından referans verilen [`Channel`](@ref) nesnesinin konumunu ve örneğini tanımlar. Serileştirilmiş `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` nesnesi (herhangi bir işçi üzerinde), dolayısıyla orijinal ile aynı arka depoya işaret eder.

Yukarıdaki kanallar örneği, aşağıda gösterildiği gibi süreçler arası iletişim için değiştirilebilir.

Dört işçi, tek bir `jobs` uzaktan kanalını işlemek için başlatılır. `job_id` ile tanımlanan işler kanala yazılır. Bu simülasyondaki her uzaktan yürütülen görev, bir `job_id` okur, rastgele bir süre bekler ve sonuçlar kanalına `job_id`, geçen süre ve kendi `pid`'sini içeren bir demet yazar. Son olarak, tüm `results` ana süreçte yazdırılır.

```julia-repl
julia> addprocs(4); # add worker processes

julia> const jobs = RemoteChannel(()->Channel{Int}(32));

julia> const results = RemoteChannel(()->Channel{Tuple}(32));

julia> @everywhere function do_work(jobs, results) # define work function everywhere
           while true
               job_id = take!(jobs)
               exec_time = rand()
               sleep(exec_time) # simulates elapsed time doing actual work
               put!(results, (job_id, exec_time, myid()))
           end
       end

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for p in workers() # start tasks on the workers to process requests in parallel
           remote_do(do_work, p, jobs, results)
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time, where = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds on worker $where")
           global n = n - 1
       end
1 finished in 0.18 seconds on worker 4
2 finished in 0.26 seconds on worker 5
6 finished in 0.12 seconds on worker 4
7 finished in 0.18 seconds on worker 4
5 finished in 0.35 seconds on worker 5
4 finished in 0.68 seconds on worker 2
3 finished in 0.73 seconds on worker 3
11 finished in 0.01 seconds on worker 3
12 finished in 0.02 seconds on worker 3
9 finished in 0.26 seconds on worker 5
8 finished in 0.57 seconds on worker 4
10 finished in 0.58 seconds on worker 2
0.055971741
```

### Remote References and Distributed Garbage Collection

Uzak referanslarla belirtilen nesneler, yalnızca kümedeki *tüm* tutulan referanslar silindiğinde serbest bırakılabilir.

Değerin saklandığı düğüm, ona hangi işçilerin referans verdiğini takip eder. Her seferinde bir [`RemoteChannel`](@ref) veya (getirilmemiş) bir [`Future`](@ref Distributed.Future) bir işçiye serileştirildiğinde, referansın işaret ettiği düğüm bilgilendirilir. Ve her seferinde bir `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` veya (getirilmemiş) bir `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` yerel olarak çöp toplanırken, değerin sahibi olan düğüm tekrar bilgilendirilir. Bu, dahili bir küme farkındalığına sahip serileştirici ile uygulanır. Uzaktan referanslar, yalnızca çalışan bir küme bağlamında geçerlidir. Normal `IO` nesnelerine referansları serileştirmek ve serileştirmeden çıkarmak desteklenmemektedir.

Bildirimler, bir referansın farklı bir işleme serileştirildiğinde "referans ekle" mesajı ve bir referans yerel olarak çöp toplandığında "referans sil" mesajı gönderilerek yapılır.

[`Future`](@ref Distributed.Future) yazma bir kez ve yerel olarak önbelleğe alındığı için, [`fetch`](@ref) işlemi, `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` değerine sahip düğümde referans izleme bilgilerini de günceller.

Değeri sahiplenen düğüm, ona yapılan tüm referanslar temizlendiğinde onu serbest bırakır.

[`Future`](@ref Distributed.Future) ile, zaten alınmış bir `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`'i farklı bir düğüme serileştirmek, değeri de gönderir çünkü orijinal uzak depolama bu süre zarfında değeri toplamış olabilir.

Önemli bir nokta, bir nesnenin yerel olarak çöp toplanmasının *ne zaman* gerçekleştiğinin nesnenin boyutuna ve sistemdeki mevcut bellek baskısına bağlı olduğudur.

Uzak referanslar durumunda, yerel referans nesnesinin boyutu oldukça küçüktür, oysa uzak düğümde saklanan değer oldukça büyük olabilir. Yerel nesne hemen toplanmayabileceğinden, [`finalize`](@ref)'yı yerel [`RemoteChannel`](@ref) örneklerinde veya alınmamış [`Future`](@ref Distributed.Future)lerde açıkça çağırmak iyi bir uygulamadır. [`fetch`](@ref)'yı bir `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` üzerinde çağırmak, aynı zamanda uzak depodan referansını kaldırdığından, alınmış `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265`ler üzerinde bu gereklidir. `4d61726b646f776e2e436f64652822222c202266696e616c697a652229_40726566`'yı açıkça çağırmak, uzak düğüme hemen bir mesaj göndererek değerine olan referansını kaldırmasını sağlar.

Bir kez kesinleştirildiğinde, bir referans geçersiz hale gelir ve herhangi bir sonraki çağrıda kullanılamaz.

## Local invocations

Veri, uzaktan düğümde yürütme için mutlaka kopyalanır. Bu, hem uzaktan çağrılar hem de verilerin farklı bir düğümde [`RemoteChannel`](@ref) / [`Future`](@ref Distributed.Future) olarak saklandığı durumlar için geçerlidir. Beklendiği gibi, bu, uzaktan düğümde serileştirilmiş nesnelerin bir kopyasını oluşturur. Ancak, hedef düğüm yerel düğüm olduğunda, yani çağıran işlem kimliği uzaktan düğüm kimliğiyle aynı olduğunda, yerel bir çağrı olarak yürütülür. Genellikle (her zaman değil) farklı bir görevde yürütülür - ancak verilerin serileştirilmesi/serileştirilmesi yapılmaz. Sonuç olarak, çağrı, geçirilen nesne örneklerine atıfta bulunur - kopyalar oluşturulmaz. Bu davranış aşağıda vurgulanmıştır:

```julia-repl
julia> using Distributed;

julia> rc = RemoteChannel(()->Channel(3));   # RemoteChannel created on local node

julia> v = [0];

julia> for i in 1:3
           v[1] = i                          # Reusing `v`
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[3], [3], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 1

julia> addprocs(1);

julia> rc = RemoteChannel(()->Channel(3), workers()[1]);   # RemoteChannel created on remote node

julia> v = [0];

julia> for i in 1:3
           v[1] = i
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[1], [2], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 3
```

Görüldüğü gibi, [`put!`](@ref) yerel olarak sahip olunan [`RemoteChannel`](@ref) ile aynı nesne `v` çağrılar arasında değiştirildiğinde, saklanan aynı tek nesne örneği ile sonuçlanır. `rc`'yi sahiplenen düğüm farklı bir düğüm olduğunda ise `v`'nin kopyaları oluşturulmaktadır.

Şunu belirtmek gerekir ki, bu genellikle bir sorun değildir. Bu, yalnızca nesnenin hem yerel olarak saklandığı hem de çağrıdan sonra değiştirildiği durumlarda dikkate alınması gereken bir durumdur. Bu tür durumlarda, nesnenin bir `deepcopy`'sini saklamak uygun olabilir.

Bu, aşağıdaki örnekte görüldüğü gibi yerel düğümdeki uzaktan aramalar için de geçerlidir:

```julia-repl
julia> using Distributed; addprocs(1);

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), myid(), v);     # Executed on local node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[1], v2=[1], true

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), workers()[1], v); # Executed on remote node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[0], v2=[1], false
```

Bir kez daha görülebileceği gibi, yerel düğüme yapılan bir uzaktan çağrı, doğrudan bir çağrı gibi davranır. Çağrı, argüman olarak geçirilen yerel nesneleri değiştirir. Uzaktan çağrıda ise, argümanların bir kopyası üzerinde işlem yapar.

Genel olarak tekrar etmek gerekirse, bu bir sorun değildir. Eğer yerel düğüm aynı zamanda bir hesaplama düğümü olarak da kullanılıyorsa ve çağrıdan sonra kullanılan argümanlar varsa, bu davranış dikkate alınmalıdır ve gerekirse yerel düğümde çağrılan işleme derin kopyalar ile argümanlar geçirilmelidir. Uzak düğümlerdeki çağrılar her zaman argümanların kopyaları üzerinde çalışacaktır.

## [Shared Arrays](@id man-shared-arrays)

Paylaşılan Diziler, birçok süreç arasında aynı diziyi eşlemek için sistem paylaşılan belleğini kullanır. [`SharedArray`](@ref) büyük miktarda verinin aynı makinedeki iki veya daha fazla süreç tarafından ortak erişilebilir olmasını istediğinizde iyi bir seçimdir. Paylaşılan Dizi desteği, tüm katılımcı işçilerde açıkça yüklenmesi gereken `SharedArrays` modülü aracılığıyla mevcuttur.

Bir tamamlayıcı veri yapısı, [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) dış paketinde bir `DArray` biçiminde sağlanmaktadır. [`SharedArray`](@ref) ile bazı benzerlikler bulunsa da, [`DArray`](https://github.com/JuliaParallel/DistributedArrays.jl) davranışı oldukça farklıdır. Bir `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` içinde, her "katılımcı" süreç tüm diziye erişim sağlar; buna karşın, bir `4d61726b646f776e2e436f64652822222c20224441727261792229_68747470733a2f2f6769746875622e636f6d2f4a756c6961506172616c6c656c2f44697374726962757465644172726179732e6a6c` içinde, her süreç yalnızca verinin bir parçasına yerel erişime sahiptir ve hiçbir iki süreç aynı parçayı paylaşmaz.

[`SharedArray`](@ref) indeksleme (atama ve değer erişimi) normal dizilerle aynı şekilde çalışır ve yerel süreç için mevcut olan temel bellek nedeniyle etkilidir. Bu nedenle, çoğu algoritma `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` üzerinde doğal olarak çalışır, ancak tek işlem modunda. Bir algoritmanın [`Array`](@ref) girişi üzerinde ısrar ettiği durumlarda, temel dizi `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566`'den [`sdata`](@ref) çağrılarak alınabilir. Diğer `AbstractArray` türleri için, `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` sadece nesneyi kendisi döndürür, bu nedenle herhangi bir `Array` türü nesnesi üzerinde `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` kullanmak güvenlidir.

Paylaşılan bir dizi için yapıcı şu biçimdedir:

```julia
SharedArray{T,N}(dims::NTuple; init=false, pids=Int[])
```

`N` boyutlu bir `T` türünde bitlerden oluşan paylaşılan bir dizi oluşturur ve bu dizinin boyutu `dims` olarak belirlenir. Bu dizi, `pids` ile belirtilen süreçler arasında paylaşılır. Dağıtılmış dizilerin aksine, bir paylaşılan dizi yalnızca `pids` adlı argümanla belirtilen katılımcı işçiler tarafından erişilebilir (ve aynı ana bilgisayarda ise oluşturan süreç tarafından da erişilebilir). Paylaşılan Dizi'de yalnızca [`isbits`](@ref) olan elemanlar desteklenmektedir.

Eğer `init` fonksiyonu, `initfn(S::SharedArray)` imzasına sahipse, bu fonksiyon tüm katılımcı işçiler üzerinde çağrılır. Her işçinin dizinin farklı bir bölümünde `init` fonksiyonunu çalıştırmasını belirtebilir, böylece başlatmayı paralelleştirebilirsiniz.

Burada kısa bir örnek:

```julia-repl
julia> using Distributed

julia> addprocs(3)
3-element Array{Int64,1}:
 2
 3
 4

julia> @everywhere using SharedArrays

julia> S = SharedArray{Int,2}((3,4), init = S -> S[localindices(S)] = repeat([myid()], length(localindices(S))))
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  3  4  4

julia> S[3,2] = 7
7

julia> S
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  7  4  4
```

[`SharedArrays.localindices`](@ref) ayrı bir boyutlu indeks aralıkları sağlar ve bazen görevleri süreçler arasında bölmek için uygundur. Elbette, işi istediğiniz şekilde bölebilirsiniz:

```julia-repl
julia> S = SharedArray{Int,2}((3,4), init = S -> S[indexpids(S):length(procs(S)):length(S)] = repeat([myid()], length( indexpids(S):length(procs(S)):length(S))))
3×4 SharedArray{Int64,2}:
 2  2  2  2
 3  3  3  3
 4  4  4  4
```

Tüm süreçlerin temel verilere erişimi olduğundan, çatışmalar oluşturmamak için dikkatli olmalısınız. Örneğin:

```julia
@sync begin
    for p in procs(S)
        @async begin
            remotecall_wait(fill!, p, S, p)
        end
    end
end
```

belirsiz davranışa yol açar. Çünkü her bir işlem, kendi `pid`'si ile *tamamen* diziyi doldurur, `S`'nin belirli bir elemanı için son olarak çalışan işlem, `pid`'sinin saklanmasına neden olacaktır.

Daha uzun ve karmaşık bir örnek olarak, aşağıdaki "çekirdek" işlemini paralel olarak çalıştırmayı düşünün:

```julia
q[i,j,t+1] = q[i,j,t] + u[i,j,t]
```

Bu durumda, işi bir boyutlu indeks kullanarak bölmeye çalışırsak, sorunlarla karşılaşma olasılığımız yüksektir: Eğer `q[i,j,t]` bir işçiye atanan bloğun sonuna yakınsa ve `q[i,j,t+1]` başka bir işçiye atanan bloğun başına yakınsa, `q[i,j,t]`'nin `q[i,j,t+1]`'i hesaplamak için gerektiği zamanda hazır olmaması çok olasıdır. Bu tür durumlarda, diziyi manuel olarak parçalara ayırmak daha iyidir. İkinci boyut boyunca bölelim. Bu işçiye atanan `(irange, jrange)` indekslerini döndüren bir fonksiyon tanımlayın:

```julia-repl
julia> @everywhere function myrange(q::SharedArray)
           idx = indexpids(q)
           if idx == 0 # This worker is not assigned a piece
               return 1:0, 1:0
           end
           nchunks = length(procs(q))
           splits = [round(Int, s) for s in range(0, stop=size(q,2), length=nchunks+1)]
           1:size(q,1), splits[idx]+1:splits[idx+1]
       end
```

Sonraki adımda çekirdek tanımlayın:

```julia-repl
julia> @everywhere function advection_chunk!(q, u, irange, jrange, trange)
           @show (irange, jrange, trange)  # display so we can see what's happening
           for t in trange, j in jrange, i in irange
               q[i,j,t+1] = q[i,j,t] + u[i,j,t]
           end
           q
       end
```

Bir `SharedArray` uygulaması için bir kullanım kolaylığı sarmalayıcısı da tanımlıyoruz.

```julia-repl
julia> @everywhere advection_shared_chunk!(q, u) =
           advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)
```

Şimdi tek bir işlemde çalışan üç farklı versiyonu karşılaştıralım:

```julia-repl
julia> advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1);
```

bir [`@distributed`](@ref) kullanan:

```julia-repl
julia> function advection_parallel!(q, u)
           for t = 1:size(q,3)-1
               @sync @distributed for j = 1:size(q,2)
                   for i = 1:size(q,1)
                       q[i,j,t+1]= q[i,j,t] + u[i,j,t]
                   end
               end
           end
           q
       end;
```

ve ve parçalara ayırarak devreden bir tane:

```julia-repl
julia> function advection_shared!(q, u)
           @sync begin
               for p in procs(q)
                   @async remotecall_wait(advection_shared_chunk!, p, q, u)
               end
           end
           q
       end;
```

Eğer `SharedArray`'lar oluşturursak ve bu fonksiyonların sürelerini ölçersek, aşağıdaki sonuçları alırız ( `julia -p 4` ile):

```julia-repl
julia> q = SharedArray{Float64,3}((500,500,500));

julia> u = SharedArray{Float64,3}((500,500,500));
```

Fonksiyonları bir kez çalıştırarak JIT derleyin ve [`@time`](@ref) ikinci çalıştırmada bunları kullanın:

```julia-repl
julia> @time advection_serial!(q, u);
(irange,jrange,trange) = (1:500,1:500,1:499)
 830.220 milliseconds (216 allocations: 13820 bytes)

julia> @time advection_parallel!(q, u);
   2.495 seconds      (3999 k allocations: 289 MB, 2.09% gc time)

julia> @time advection_shared!(q,u);
        From worker 2:       (irange,jrange,trange) = (1:500,1:125,1:499)
        From worker 4:       (irange,jrange,trange) = (1:500,251:375,1:499)
        From worker 3:       (irange,jrange,trange) = (1:500,126:250,1:499)
        From worker 5:       (irange,jrange,trange) = (1:500,376:500,1:499)
 238.119 milliseconds (2264 allocations: 169 KB)
```

`advection_shared!`'ın en büyük avantajı, işçiler arasında trafiği en aza indirmesi ve her birinin atanan parça üzerinde uzun süre hesaplama yapmasına olanak tanımasıdır.

### Shared Arrays and Distributed Garbage Collection

Uzak referanslar gibi, paylaşılan diziler de tüm katılımcı işçilerden referansları serbest bırakmak için oluşturma düğümündeki çöp toplama işlemine bağımlıdır. Birçok kısa ömürlü paylaşılan dizi nesnesi oluşturan kod, bu nesneleri mümkün olan en kısa sürede açıkça sonlandırmaktan fayda sağlayacaktır. Bu, hem bellek hem de paylaşılan segmenti haritalayan dosya tanıtıcılarının daha erken serbest bırakılmasını sağlar.

## ClusterManagers

Julia süreçlerinin başlatılması, yönetimi ve mantıksal bir kümeye ağ bağlantısı, küme yöneticileri aracılığıyla yapılır. Bir `ClusterManager`, aşağıdakilerden sorumludur:

  * küme ortamında işçi süreçlerini başlatma
  * her çalışanın yaşam döngüsü boyunca etkinlikleri yönetmek
  * isteğe bağlı olarak, veri taşımayı sağlama

Bir Julia kümesinin aşağıdaki özellikleri vardır:

  * İlk Julia süreci, aynı zamanda `master` olarak da adlandırılır, özel bir süreçtir ve `id`'si 1'dir.
  * Sadece `master` süreci işçi süreçleri ekleyebilir veya kaldırabilir.
  * Tüm süreçler doğrudan birbirleriyle iletişim kurabilir.

Çalışanlar arasındaki bağlantılar (yerleşik TCP/IP taşıma kullanılarak) aşağıdaki şekilde kurulmaktadır:

  * [`addprocs`](@ref) ana `ClusterManager` nesnesi ile ana süreçte çağrılır.
  * [`addprocs`](@ref) uygun [`launch`](@ref) yöntemini çağırır ve uygun makinelerde gerekli sayıda işçi süreci oluşturur.
  * Her bir işçi, boş bir portta dinlemeye başlar ve ana bilgisayar ve port bilgilerini [`stdout`](@ref) dosyasına yazar.
  * Küme yöneticisi, her işçinin [`stdout`](@ref) değerini yakalar ve bunu ana işleme sunar.
  * Ana süreç bu bilgiyi ayrıştırır ve her bir işçiye TCP/IP bağlantıları kurar.
  * Her işçi, kümedeki diğer işçiler hakkında da bilgilendirilir.
  * Her işçi, kendi `id`'sinden daha küçük olan tüm işçilere bağlanır.
  * Bu şekilde her işçinin doğrudan diğer her işçiyle bağlantılı olduğu bir mesh ağı kurulmuş olur.

Varsayılan taşıma katmanı, düz [`TCPSocket`](@ref) kullanırken, bir Julia kümesinin kendi taşımasını sağlaması mümkündür.

Julia, iki yerleşik küme yöneticisi sağlar:

  * `LocalManager`, [`addprocs()`](@ref) veya [`addprocs(np::Integer)`](@ref) çağrıldığında kullanılır.
  * `SSHManager`, [`addprocs(hostnames::Array)`](@ref) ile bir dizi ana bilgisayar adı ile çağrıldığında kullanılır.

`LocalManager`, aynı ana makinede ek işçi başlatmak için kullanılır ve böylece çok çekirdekli ve çok işlemcili donanımdan yararlanır.

Böylece, minimal bir küme yöneticisinin şunları yapması gerekecektir:

  * soy bir alt türü `ClusterManager` soyut.
  * [`launch`](@ref) metodunu uygulayın, yeni işçileri başlatmaktan sorumlu bir yöntem.
  * [`manage`](@ref)'yı uygulayın, bu bir çalışanın yaşam döngüsü boyunca çeşitli olaylar sırasında çağrılır (örneğin, bir kesme sinyali gönderme).

[`addprocs(manager::FooManager)`](@ref addprocs) `FooManager`'ın uygulaması için gereklidir:

```julia
function launch(manager::FooManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

Bir örnek olarak, aynı ana bilgisayarda işçi başlatmaktan sorumlu `LocalManager`'ın nasıl uygulandığına bakalım:

```julia
struct LocalManager <: ClusterManager
    np::Integer
end

function launch(manager::LocalManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::LocalManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

[`launch`](@ref) yöntemi aşağıdaki argümanları alır:

  * `manager::ClusterManager`: [`addprocs`](@ref) ile çağrılan küme yöneticisi
  * `params::Dict`: [`addprocs`](@ref)'ya geçirilen tüm anahtar kelime argümanları
  * `launched::Array`: bir veya daha fazla `WorkerConfig` nesnesini eklemek için dizi
  * `c::Condition`: işçiler başlatıldıkça bildirilmesi gereken durum değişkeni

[`launch`](@ref) yöntemi ayrı bir görevde asenkron olarak çağrılır. Bu görevin sona ermesi, talep edilen tüm işçilerin başlatıldığını gösterir. Bu nedenle `4d61726b646f776e2e436f64652822222c20226c61756e63682229_40726566` fonksiyonu, talep edilen tüm işçilerin başlatıldığı anda çıkmalıdır.

Yeni başlatılan işçiler, birbirleriyle ve ana işlemle her yöne bağlantılıdır. Komut satırı argümanı `--worker[=<cookie>]` belirtmek, başlatılan süreçlerin kendilerini işçi olarak başlatmalarına ve bağlantıların TCP/IP soketleri aracılığıyla kurulmasına neden olur.

Tüm kümedeki işçiler, ana makine ile aynı [cookie](@ref man-cluster-cookie) değerini paylaşır. Çerez belirtilmediğinde, yani `--worker` seçeneği ile, işçi bunu standart girdisinden okumaya çalışır. `LocalManager` ve `SSHManager`, her ikisi de çerezi yeni başlatılan işçilere standart girdileri aracılığıyla iletir.

Varsayılan olarak, bir işçi, [`getipaddr()`](@ref) çağrısının döndürdüğü adreste boş bir portta dinleyecektir. Dinlenecek belirli bir adres, isteğe bağlı `--bind-to bind_addr[:port]` argümanı ile belirtilebilir. Bu, çoklu ev sahibi olan sunucular için faydalıdır.

Bir TCP/IP dışı taşıma örneği olarak, bir uygulama MPI kullanmayı seçebilir; bu durumda `--worker` belirtilmemelidir. Bunun yerine, yeni başlatılan işçiler, paralel yapıları kullanmadan önce `init_worker(cookie)` çağrısını yapmalıdır.

Herhangi bir başlatılan işçi için, [`launch`](@ref) yöntemi `launched`'a (uygun alanlar başlatılmış şekilde) bir `WorkerConfig` nesnesi eklemelidir.

```julia
mutable struct WorkerConfig
    # Common fields relevant to all cluster managers
    io::Union{IO, Nothing}
    host::Union{AbstractString, Nothing}
    port::Union{Integer, Nothing}

    # Used when launching additional workers at a host
    count::Union{Int, Symbol, Nothing}
    exename::Union{AbstractString, Cmd, Nothing}
    exeflags::Union{Cmd, Nothing}

    # External cluster managers can use this to store information at a per-worker level
    # Can be a dict if multiple fields need to be stored.
    userdata::Any

    # SSHManager / SSH tunnel connections to workers
    tunnel::Union{Bool, Nothing}
    bind_addr::Union{AbstractString, Nothing}
    sshflags::Union{Cmd, Nothing}
    max_parallel::Union{Integer, Nothing}

    # Used by Local/SSH managers
    connect_at::Any

    [...]
end
```

`WorkerConfig` içindeki alanların çoğu yerleşik yöneticiler tarafından kullanılır. Özel küme yöneticileri genellikle yalnızca `io` veya `host` / `port` belirtir:

  * Eğer `io` belirtilmişse, ana bilgisayar/port bilgilerini okumak için kullanılır. Bir Julia işçisi başlatıldığında kendi bağlanma adresini ve portunu yazdırır. Bu, Julia işçilerinin manuel olarak yapılandırılması gereken işçi portları yerine mevcut olan herhangi bir boş portta dinlemesine olanak tanır.
  * Eğer `io` belirtilmemişse, bağlanmak için `host` ve `port` kullanılır.
  * `count`, `exename` ve `exeflags`, bir işçiden ek işçiler başlatmak için gereklidir. Örneğin, bir küme yöneticisi her düğüm için tek bir işçi başlatabilir ve bunu ek işçiler başlatmak için kullanabilir.

      * `count` ile bir tamsayı değeri `n` toplamda `n` işçi başlatacaktır.
      * `count` değeri `:auto` olduğunda, o makinedeki CPU iş parçacığı (mantıksal çekirdek) sayısı kadar işçi başlatılacaktır.
      * `exename`, `julia` yürütülebilir dosyasının tam yolu da dahil olmak üzere adıdır.
      * `exeflags` yeni işçiler için gerekli komut satırı argümanlarına ayarlanmalıdır.
  * `tunnel`, `bind_addr`, `sshflags` ve `max_parallel`, ana süreçten işçilere bağlanmak için bir ssh tüneli gerektiğinde kullanılır.
  * `userdata`, özel küme yöneticilerinin kendi işçi-spesifik bilgilerini saklaması için sağlanmıştır.

`manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)` işçi ömrü boyunca uygun `op` değerleri ile farklı zamanlarda çağrılır:

  * `:register`/`:deregister` ile bir işçi Julia işçi havuzuna eklendiğinde / kaldırıldığında.
  * `interrupt` çağrıldığında `interrupt(workers)` ile. `ClusterManager`, uygun işçiye bir kesme sinyali göndermelidir.
  * temizlik amaçları için `:finalize` ile.

### Cluster Managers with Custom Transports

Varsayılan TCP/IP tümden tümü soket bağlantılarını özel bir taşıma katmanı ile değiştirmek biraz daha karmaşıktır. Her Julia süreci, bağlı olduğu işçi sayısı kadar iletişim görevine sahiptir. Örneğin, tümden tümü bir ağda 32 süreçten oluşan bir Julia kümesini düşünün:

  * Her bir Julia süreci bu nedenle 31 iletişim görevi vardır.
  * Her görev, bir mesaj işleme döngüsünde tek bir uzaktan çalışandan gelen tüm gelen mesajları işler.
  * Mesaj işleme döngüsü bir `IO` nesnesini bekler (örneğin, varsayılan uygulamada bir [`TCPSocket`](@ref)), tüm bir mesajı okur, işler ve bir sonraki mesajı bekler.
  * Bir işlemi mesaj göndermek, herhangi bir Julia görevi üzerinden doğrudan yapılır - sadece iletişim görevleri değil - yine uygun `IO` nesnesi aracılığıyla.

Varsayılan taşıyıcının değiştirilmesi, yeni uygulamanın uzak işçilere bağlantılar kurmasını ve mesaj işleme döngülerinin bekleyebileceği uygun `IO` nesnelerini sağlamasını gerektirir. Uygulanması gereken yöneticinin özel geri çağırmaları şunlardır:

```julia
connect(manager::FooManager, pid::Integer, config::WorkerConfig)
kill(manager::FooManager, pid::Int, config::WorkerConfig)
```

Varsayılan uygulama (TCP/IP soketlerini kullanan) `connect(manager::ClusterManager, pid::Integer, config::WorkerConfig)` olarak uygulanmıştır.

`connect`, bir `pid` işçisinden gönderilen verileri okumak için bir `IO` nesnesi ve `pid` işçisine gönderilmesi gereken verileri yazmak için bir diğer `IO` nesnesi döndürmelidir. Özel küme yöneticileri, özel, muhtemelen `IO` olmayan taşıma ile Julia'nın yerleşik paralel altyapısı arasında veri iletmek için bir bellek içi `BufferStream` kullanabilir.

Bir `BufferStream`, asenkron olarak işlenebilen bir akış olan `IO` gibi davranan, bellek içi bir [`IOBuffer`](@ref)'dır.

`clustermanager/0mq` klasörü [Examples repository](https://github.com/JuliaAttic/Examples) içinde, ortada bir 0MQ aracısı ile yıldız topolojisinde Julia işçilerini bağlamak için ZeroMQ kullanma örneği bulunmaktadır. Not: Julia süreçleri hala birbirine *mantıksal* olarak bağlıdır - herhangi bir işçi, 0MQ'nun taşıma katmanı olarak kullanıldığını bilmeden, doğrudan herhangi bir diğer işçiye mesaj gönderebilir.

Özel taşıma yöntemleri kullanırken:

  * Julia işçileri `--worker` ile başlatılmamalıdır. `--worker` ile başlatmak, yeni başlatılan işçilerin varsayılan olarak TCP/IP soket taşıma uygulamasını kullanmasına neden olacaktır.
  * Her gelen mantıksal bağlantı için bir işçi ile, `Base.process_messages(rd::IO, wr::IO)()` çağrılmalıdır. Bu, `IO` nesneleri tarafından temsil edilen işçiden gelen ve giden mesajların okunması ve yazılmasıyla ilgilenen yeni bir görevi başlatır.
  * `init_worker(cookie, manager::FooManager)` *çalışan süreç başlatma* işleminin bir parçası olarak *zorunlu* olarak çağrılmalıdır.
  * `WorkerConfig` içindeki `connect_at::Any` alanı, [`launch`](@ref) çağrıldığında küme yöneticisi tarafından ayarlanabilir. Bu alanın değeri, tüm [`connect`](@ref) geri çağırmalarında iletilir. Genellikle, bir işçiye *nasıl bağlanılacağı* hakkında bilgi taşır. Örneğin, TCP/IP soket taşıma yöntemi, bir işçiye bağlanmak için `(host, port)` demetini belirtmek üzere bu alanı kullanır.

`kill(manager, pid, config)` işçi kümeden kaldırmak için çağrılır. Ana süreçte, ilgili `IO` nesneleri, uygun temizliği sağlamak için uygulama tarafından kapatılmalıdır. Varsayılan uygulama, belirtilen uzak işçi üzerinde basitçe bir `exit()` çağrısı gerçekleştirir.

Örnekler klasörü `clustermanager/simple`, küme kurulumu için UNIX alan soketlerini kullanan basit bir uygulamayı gösteren bir örnektir.

### Network Requirements for LocalManager and SSHManager

Julia kümeleri, yerel dizüstü bilgisayarlar, bölüm kümeleri veya hatta bulut gibi güvenli ortamlarda çalıştırılmak üzere tasarlanmıştır. Bu bölüm, yerleşik `LocalManager` ve `SSHManager` için ağ güvenliği gereksinimlerini kapsar:

  * Ana süreç herhangi bir portta dinlemez. Sadece işçilere bağlanır.
  * Her bir işçi yalnızca yerel arayüzlerden birine bağlanır ve işletim sistemi tarafından atanan geçici bir port numarasını dinler.
  * `LocalManager`, `addprocs(N)` tarafından kullanıldığında, varsayılan olarak yalnızca döngü geri arayüzüne bağlanır. Bu, daha sonra uzaktan ana bilgisayarlarda (veya kötü niyetli niyetleri olan herhangi biri tarafından) başlatılan işçilerin kümeye bağlanamayacağı anlamına gelir. `addprocs(4)` ardından `addprocs(["remote_host"])` başarısız olacaktır. Bazı kullanıcılar, yerel sistemleri ve birkaç uzaktan sistemi içeren bir küme oluşturmak isteyebilir. Bu, `LocalManager`'ın dış bir ağ arayüzüne bağlanmasını açıkça talep ederek yapılabilir; `addprocs(4; restrict=false)`.
  * `SSHManager`, `addprocs(list_of_remote_hosts)` tarafından kullanılan, uzaktaki ana bilgisayarlarda işçi başlatmak için SSH üzerinden çalışır. Varsayılan olarak, SSH yalnızca Julia işçilerini başlatmak için kullanılır. Sonraki ana-işçi ve işçi-işçi bağlantıları düz, şifrelenmemiş TCP/IP soketlerini kullanır. Uzaktaki ana bilgisayarlarda şifresiz giriş etkin olmalıdır. Ek SSH bayrakları veya kimlik bilgileri `sshflags` anahtar argümanı aracılığıyla belirtilebilir.
  * `addprocs(list_of_remote_hosts; tunnel=true, sshflags=<ssh keys and other flags>)` SSH bağlantılarını master-worker için kullanmak istediğimizde faydalıdır. Bunun tipik bir senaryosu, Julia REPL (yani, master) çalıştıran yerel bir dizüstü bilgisayarın, geri kalan kümenin bulutta, örneğin Amazon EC2 üzerinde olmasıdır. Bu durumda, uzak kümede yalnızca 22 numaralı portun açılması gerekir ve SSH istemcisi, kamu anahtarı altyapısı (PKI) aracılığıyla kimlik doğrulaması yapılmalıdır. Kimlik doğrulama bilgileri `sshflags` aracılığıyla sağlanabilir, örneğin ```sshflags=`-i <keyfile>` ```.

    Tüm işçilerin birbirine düz TCP soketleri aracılığıyla bağlandığı bir tüm-e-tüm topolojisinde (varsayılan), küme düğümlerindeki güvenlik politikası, işçiler arasında geçici port aralığı (işletim sistemine göre değişir) için serbest bağlantıyı sağlamalıdır.

    Tüm işçi-işçi trafiğini (SSH üzerinden) güvence altına almak ve şifrelemek veya bireysel mesajları şifrelemek, özel bir `ClusterManager` aracılığıyla yapılabilir.
  * Eğer `multiplex=true` seçeneğini [`addprocs`](@ref) için belirtirseniz, SSH çoklama, ana ve işçiler arasında bir tünel oluşturmak için kullanılır. Eğer SSH çoklamayı kendiniz yapılandırdıysanız ve bağlantı zaten kurulmuşsa, `multiplex` seçeneğinden bağımsız olarak SSH çoklama kullanılır. Çoklama etkinleştirildiğinde, mevcut bağlantı kullanılarak yönlendirme ayarlanır (`ssh` içindeki `-O forward` seçeneği). Bu, sunucularınızın şifre kimlik doğrulaması gerektirmesi durumunda faydalıdır; `4d61726b646f776e2e436f64652822222c202261646470726f63732229_40726566` öncesinde sunucuya giriş yaparak Julia'da kimlik doğrulamasını atlayabilirsiniz. Kontrol soketi oturum sırasında `~/.ssh/julia-%r@%h:%p` konumunda bulunacaktır, mevcut çoklama bağlantısı kullanılmadığı sürece. Bir düğümde birden fazla işlem oluşturup çoklamayı etkinleştirirseniz, bant genişliğinin sınırlı olabileceğini unutmayın, çünkü bu durumda işlemler tek bir çoklama TCP bağlantısını paylaşır.

### [Cluster Cookie](@id man-cluster-cookie)

Tüm kümedeki işlemler, varsayılan olarak ana işlemde rastgele oluşturulmuş bir dize olan aynı çerezi paylaşır:

  * [`cluster_cookie()`](@ref) çerezi dönerken, `cluster_cookie(cookie)()` onu ayarlar ve yeni çerezi döner.
  * Tüm bağlantılar, yalnızca ana tarafından başlatılan işçilerin birbirine bağlanmasına izin vermek için her iki tarafta da kimlik doğrulaması yapılır.
  * Çerez, başlangıçta `--worker=<cookie>` argümanı aracılığıyla işçilere geçirilebilir. Eğer `--worker` argümanı çerez olmadan belirtilirse, işçi çerezi standart girişinden okumaya çalışır ([`stdin`](@ref)). Çerez alındıktan sonra `stdin` hemen kapatılır.
  * `ClusterManager`'lar, [`cluster_cookie()`](@ref) çağrısını yaparak ana makinedeki çerezi alabilirler. Varsayılan TCP/IP taşımasını kullanmayan (ve dolayısıyla `--worker` belirtmeyen) küme yöneticileri, ana makinedeki ile aynı çerezi kullanarak `init_worker(cookie, manager)` çağrısını yapmalıdır.

Güvenlik seviyesinin daha yüksek olduğu ortamların bunu özel bir `ClusterManager` aracılığıyla uygulayabileceğini unutmayın. Örneğin, çerezler önceden paylaşılabilir ve bu nedenle bir başlangıç argümanı olarak belirtilmez.

## Specifying Network Topology (Experimental)

`topology` anahtar kelime argümanı, [`addprocs`](@ref) fonksiyonuna geçildiğinde, işçilerin birbirine nasıl bağlanması gerektiğini belirtmek için kullanılır:

  * `:all_to_all`, varsayılan: tüm işçiler birbirine bağlıdır.
  * `:master_worker`: yalnızca sürücü süreci, yani `pid` 1, işçilere bağlantılara sahiptir.
  * `:custom`: küme yöneticisinin `launch` yöntemi, `WorkerConfig` içindeki `ident` ve `connect_idents` alanları aracılığıyla bağlantı topolojisini belirtir. Küme yöneticisi tarafından sağlanan bir kimliğe (`ident`) sahip bir işçi, `connect_idents` içinde belirtilen tüm işçilere bağlanacaktır.

Anahtar argümanı `lazy=true|false` yalnızca `topology` seçeneği `:all_to_all` üzerinde etkilidir. Eğer `true` ise, küme, ana bilgisayarın tüm işçilere bağlı olduğu şekilde başlar. Belirli işçi-işçi bağlantıları, iki işçi arasında ilk uzaktan çağrı yapıldığında kurulur. Bu, küme içi iletişim için tahsis edilen başlangıç kaynaklarını azaltmaya yardımcı olur. Bağlantılar, paralel bir programın çalışma zamanı gereksinimlerine bağlı olarak kurulur. `lazy` için varsayılan değer `true`'dur.

Şu anda, bağlantısız işçiler arasında bir mesaj göndermek bir hataya neden olmaktadır. Bu davranış, işlevsellik ve arayüz ile birlikte, deneysel bir nitelik olarak değerlendirilmelidir ve gelecekteki sürümlerde değişebilir.

## Noteworthy external packages

Julia paralelliği dışında bahsedilmesi gereken birçok harici paket bulunmaktadır. Örneğin, [`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) `MPI` protokolü için bir Julia sarmalayıcısıdır, [`Dagger.jl`](https://github.com/JuliaParallel/Dagger.jl) Python'un [Dask](https://dask.org/) ile benzer işlevsellik sağlar ve [`DistributedArrays.jl`](https://github.com/JuliaParallel/Distributedarrays.jl) işçiler arasında dağıtılmış dizi işlemleri sağlar, [outlined above](@ref man-shared-arrays) gibi.

Julia'nın GPU programlama ekosistemine bir atıfta bulunulmalıdır, bu şunları içerir:

1. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) çeşitli CUDA kütüphanelerini sarar ve Nvidia GPU'lar için Julia çekirdeklerini derlemeyi destekler.
2. [oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl), oneAPI birleşik programlama modelini sarar ve desteklenen hızlandırıcılarda Julia çekirdeklerini çalıştırmayı destekler. Şu anda yalnızca Linux desteklenmektedir.
3. [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl) AMD ROCm kütüphanelerini sarar ve AMD GPU'lar için Julia çekirdeklerini derlemeyi destekler. Şu anda yalnızca Linux desteklenmektedir.
4. Yüksek seviyeli kütüphaneler gibi [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl), [Tullio.jl](https://github.com/mcabbott/Tullio.jl) ve [ArrayFire.jl](https://github.com/JuliaComputing/ArrayFire.jl).

Aşağıdaki örnekte, bir diziyi birden fazla işlem arasında dağıtmak için hem `DistributedArrays.jl` hem de `CUDA.jl` kullanacağız; önce `distribute()` ve `CuArray()` ile dönüştürerek.

`DistributedArrays.jl`'yi tüm süreçler boyunca [`@everywhere`](@ref) kullanarak içe aktarmayı unutmayın.

```julia-repl
$ ./julia -p 4

julia> addprocs()

julia> @everywhere using DistributedArrays

julia> using CUDA

julia> B = ones(10_000) ./ 2;

julia> A = ones(10_000) .* π;

julia> C = 2 .* A ./ B;

julia> all(C .≈ 4*π)
true

julia> typeof(C)
Array{Float64,1}

julia> dB = distribute(B);

julia> dA = distribute(A);

julia> dC = 2 .* dA ./ dB;

julia> all(dC .≈ 4*π)
true

julia> typeof(dC)
DistributedArrays.DArray{Float64,1,Array{Float64,1}}

julia> cuB = CuArray(B);

julia> cuA = CuArray(A);

julia> cuC = 2 .* cuA ./ cuB;

julia> all(cuC .≈ 4*π);
true

julia> typeof(cuC)
CuArray{Float64,1}
```

Aşağıdaki örnekte, bir diziyi birden fazla işlem arasında dağıtmak ve üzerinde genel bir işlev çağırmak için hem `DistributedArrays.jl` hem de `CUDA.jl` kullanacağız.

```julia
function power_method(M, v)
    for i in 1:100
        v = M*v
        v /= norm(v)
    end

    return v, norm(M*v) / norm(v)  # or  (M*v) ./ v
end
```

`power_method` sürekli yeni bir vektör oluşturur ve onu normalize eder. Fonksiyon bildiriminde herhangi bir tür imzası belirtmedik, yukarıda bahsedilen veri türleriyle çalışıp çalışmadığına bakalım:

```julia-repl
julia> M = [2. 1; 1 1];

julia> v = rand(2)
2-element Array{Float64,1}:
0.40395
0.445877

julia> power_method(M,v)
([0.850651, 0.525731], 2.618033988749895)

julia> cuM = CuArray(M);

julia> cuv = CuArray(v);

julia> curesult = power_method(cuM, cuv);

julia> typeof(curesult)
CuArray{Float64,1}

julia> dM = distribute(M);

julia> dv = distribute(v);

julia> dC = power_method(dM, dv);

julia> typeof(dC)
Tuple{DistributedArrays.DArray{Float64,1,Array{Float64,1}},Float64}
```

Bu kısa dış paketlere maruz kalmayı sona erdirmek için, MPI protokolünün bir Julia sarmalayıcısı olan `MPI.jl`'yi göz önünde bulundurabiliriz. Her bir iç işlevi ele almak çok uzun süreceğinden, protokolü uygulamak için kullanılan yaklaşımı basitçe takdir etmek daha iyi olacaktır.

Bu oyuncak betiği düşünün, bu basitçe her alt süreci çağırır, sırasını oluşturur ve ana işleme ulaşıldığında, sıraların toplamını gerçekleştirir.

```julia
import MPI

MPI.Init()

comm = MPI.COMM_WORLD
MPI.Barrier(comm)

root = 0
r = MPI.Comm_rank(comm)

sr = MPI.Reduce(r, MPI.SUM, root, comm)

if(MPI.Comm_rank(comm) == root)
   @printf("sum of ranks: %s\n", sr)
end

MPI.Finalize()
```

```
mpirun -np 4 ./julia example.jl
```

[^1]: In this context, MPI refers to the MPI-1 standard. Beginning with MPI-2, the MPI standards committee introduced a new set of communication mechanisms, collectively referred to as Remote Memory Access (RMA). The motivation for adding rma to the MPI standard was to facilitate one-sided communication patterns. For additional information on the latest MPI standard, see [https://mpi-forum.org/docs](https://mpi-forum.org/docs).
