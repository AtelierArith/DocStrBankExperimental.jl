# [Asynchronous Programming](@id man-asynchronous)

Bir program dış dünya ile etkileşime girmesi gerektiğinde, örneğin internet üzerinden başka bir makine ile iletişim kurarken, programdaki işlemlerin öngörülemeyen bir sırada gerçekleşmesi gerekebilir. Diyelim ki programınız bir dosyayı indirmesi gerekiyor. İndirme işlemini başlatmak, tamamlanmasını beklerken diğer işlemleri gerçekleştirmek ve ardından indirilen dosyaya ihtiyaç duyan kodu, dosya mevcut olduğunda yeniden başlatmak istiyoruz. Bu tür bir senaryo, bazen eşzamanlı programlama olarak da adlandırılan asenkron programlama alanına girer (çünkü kavramsal olarak, birden fazla şey aynı anda gerçekleşiyor).

Bu senaryoları ele almak için Julia, [`Task`](@ref) (aynı zamanda simetrik korutinler, hafif iş parçacıkları, işbirlikçi çoklu görev veya tek seferlik devamlar gibi çeşitli diğer adlarla da bilinir) sağlar. Bir hesaplama işi (pratikte, belirli bir işlevin yürütülmesi) `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` olarak belirlendiğinde, başka bir `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`'ya geçerek onu kesmek mümkün hale gelir. Orijinal `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` daha sonra yeniden başlatılabilir; bu noktada, kaldığı yerden devam eder. Başlangıçta, bu bir işlev çağrısına benzer görünebilir. Ancak iki ana fark vardır. İlk olarak, görev değiştirme herhangi bir alan kullanmaz, bu nedenle herhangi bir sayıda görev değişimi, çağrı yığınını tüketmeden gerçekleşebilir. İkincisi, görevler arasında geçiş herhangi bir sırayla gerçekleşebilir; oysa işlev çağrılarında, çağrılan işlevin yürütülmesi tamamlanmadan kontrol çağıran işleve dönemez.

## Basic `Task` operations

Bir `Task`'ı, yerine getirilmesi gereken bir hesaplama işinin bir tutamağı olarak düşünebilirsiniz. Bir create-start-run-finish yaşam döngüsüne sahiptir. Görevler, çalıştırılacak 0-argümanlı bir fonksiyon üzerinde `Task` yapıcısını çağırarak veya [`@task`](@ref) makrosunu kullanarak oluşturulur:

```julia-repl
julia> t = @task begin; sleep(5); println("done"); end
Task (runnable) @0x00007f13a40c0eb0
```

`@task x` `Task(()->x)` ile eşdeğerdir.

Bu görev beş saniye bekleyecek ve ardından `done` yazdıracak. Ancak henüz çalışmaya başlamadı. Hazır olduğumuzda [`schedule`](@ref) çağrısını yaparak çalıştırabiliriz:

```julia-repl
julia> schedule(t);
```

Eğer bunu REPL'de denerseniz, `schedule`'ın hemen döndüğünü göreceksiniz. Bunun nedeni, `t`'yi çalıştırılacak görevlerin içsel bir kuyruğuna eklemesidir. Ardından, REPL bir sonraki istemi yazdıracak ve daha fazla girdi bekleyecektir. Klavye girişi beklemek, diğer görevlerin çalışması için bir fırsat sağlar, bu nedenle o noktada `t` başlayacaktır. `t`, [`sleep`](@ref)'yı çağırır, bu da bir zamanlayıcı ayarlar ve yürütmeyi durdurur. Eğer başka görevler planlandıysa, o zaman çalışabilirler. Beş saniye sonra, zamanlayıcı tetiklenir ve `t`'yi yeniden başlatır, ve `done` yazdırıldığını göreceksiniz. `t` tamamlanmış olur.

[`wait`](@ref) işlevi, başka bir görev bitene kadar çağrılan görevi engeller. Örneğin, eğer yazarsanız

```julia-repl
julia> schedule(t); wait(t)
```

sadece `schedule` çağırmak yerine, bir sonraki girdi istemi görünmeden önce beş saniyelik bir duraklama göreceksiniz. Bunun nedeni, REPL'nin ilerlemeden önce `t`'nin bitmesini beklemesidir.

Görev oluşturmak ve hemen planlamak istemek yaygındır, bu nedenle bu amaçla [`@async`](@ref) makrosu sağlanmıştır –- `@async x`, `schedule(@task x)` ile eşdeğerdir.

## Communicating with Channels

Bazı problemler, gerekli işlerin çeşitli parçalarının işlev çağrılarıyla doğal olarak ilişkili olmadığı durumları içerir; yapılması gereken işler arasında belirgin bir "çağıran" veya "çağrılan" yoktur. Bir örnek, bir karmaşık prosedürün değerler ürettiği ve başka bir karmaşık prosedürün bunları tükettiği üretici-tüketici problemidir. Tüketici, bir değer almak için basitçe bir üretici işlevini çağırmakta zorlanır, çünkü üreticinin daha fazla değer üretmesi gerekebilir ve bu nedenle henüz geri dönmeye hazır olmayabilir. Görevlerle, üretici ve tüketici ihtiyaç duydukları sürece çalışabilir, değerleri gerektiği gibi karşılıklı olarak iletebilirler.

Julia, bu problemi çözmek için bir [`Channel`](@ref) mekanizması sağlar. Bir `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`, birden fazla görevin okuma ve yazma yapabileceği beklenebilir bir ilk giren ilk çıkar kuyruğudur.

Bir üretici görevini tanımlayalım; bu görev, [`put!`](@ref) çağrısı aracılığıyla değerler üretir. Değerleri tüketmek için, üreticiyi yeni bir görevde çalışacak şekilde planlamamız gerekir. Bir argüman olarak 1-arg fonksiyonu kabul eden özel bir [`Channel`](@ref) yapıcısı, bir kanala bağlı bir görevi çalıştırmak için kullanılabilir. Daha sonra, kanal nesnesinden değerleri tekrar tekrar [`take!`](@ref) alabiliriz:

```jldoctest producer
julia> function producer(c::Channel)
           put!(c, "start")
           for n=1:4
               put!(c, 2n)
           end
           put!(c, "stop")
       end;

julia> chnl = Channel(producer);

julia> take!(chnl)
"start"

julia> take!(chnl)
2

julia> take!(chnl)
4

julia> take!(chnl)
6

julia> take!(chnl)
8

julia> take!(chnl)
"stop"
```

Bu davranışı düşünmenin bir yolu, `producer`'ın birden fazla kez dönebilmesidir. [`put!`](@ref) çağrıları arasında, üreticinin yürütülmesi askıya alınır ve tüketici kontrolü eline alır.

Dönen [`Channel`](@ref) bir `for` döngüsünde yineleyici bir nesne olarak kullanılabilir; bu durumda döngü değişkeni üretilen tüm değerleri alır. Döngü, kanal kapandığında sona erer.

```jldoctest producer
julia> for x in Channel(producer)
           println(x)
       end
start
2
4
6
8
stop
```

Not edin ki üreticide kanalı açıkça kapatmamıza gerek yoktu. Bunun nedeni, [`Channel`](@ref) nesnesinin [`Task`](@ref) nesnesine bağlanmasının, bir kanalın açık yaşam süresini bağlı görevle ilişkilendirmesidir. Görev sona erdiğinde kanal nesnesi otomatik olarak kapatılır. Birden fazla kanal bir göreve bağlanabilir ve tersine.

[`Task`](@ref) yapıcısı 0-argüman fonksiyonu beklerken, [`Channel`](@ref) metodu bir görev bağlı kanal oluşturan, `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` türünde tek bir argüman kabul eden bir fonksiyon bekler. Yaygın bir desen, üreticinin parametreli olmasıdır; bu durumda 0 veya 1 argümanlı [anonymous function](@ref man-anonymous-functions) oluşturmak için kısmi fonksiyon uygulaması gereklidir.

[`Task`](@ref) nesneleri için bu doğrudan veya bir kolaylık makrosu kullanılarak yapılabilir:

```julia
function mytask(myarg)
    ...
end

taskHdl = Task(() -> mytask(7))
# or, equivalently
taskHdl = @task mytask(7)
```

Daha gelişmiş iş dağıtım desenlerini düzenlemek için, [`bind`](@ref) ve [`schedule`](@ref) [`Task`](@ref) ve [`Channel`](@ref) yapıcıları ile birlikte kullanılabilir, böylece bir dizi kanalı bir dizi üretici/tüketici görevine açıkça bağlayabilirsiniz.

### More on Channels

Bir kanal bir boru olarak görselleştirilebilir, yani bir yazma ucu ve bir okuma ucu vardır:

  * Farklı görevlerde birden fazla yazar, [`put!`](@ref) çağrıları aracılığıyla aynı kanala eşzamanlı olarak yazabilir.
  * Farklı görevlerde birden fazla okuyucu, [`take!`](@ref) çağrıları aracılığıyla verileri eşzamanlı olarak okuyabilir.
  * Örnek olarak:

    ```julia
    # Given Channels c1 and c2,
    c1 = Channel(32)
    c2 = Channel(32)

    # and a function `foo` which reads items from c1, processes the item read
    # and writes a result to c2,
    function foo()
        while true
            data = take!(c1)
            [...]               # process data
            put!(c2, result)    # write out result
        end
    end

    # we can schedule `n` instances of `foo` to be active concurrently.
    for _ in 1:n
        errormonitor(@async foo())
    end
    ```
  * Kanallar `Channel{T}(sz)` yapıcısı aracılığıyla oluşturulur. Kanal yalnızca `T` türündeki nesneleri tutacaktır. Tür belirtilmezse, kanal herhangi bir türde nesneleri tutabilir. `sz`, kanalın her zaman tutabileceği maksimum eleman sayısını ifade eder. Örneğin, `Channel(32)` herhangi bir türde maksimum 32 nesne tutabilen bir kanal oluşturur. `Channel{MyType}(64)` her zaman `MyType` türünde en fazla 64 nesne tutabilir.
  * Eğer bir [`Channel`](@ref) boşsa, okuyucular (bir [`take!`](@ref) çağrısında) veri mevcut olana kadar engellenecektir.
  * Eğer bir [`Channel`](@ref) doluysa, yazarlar (bir [`put!`](@ref) çağrısında) alan mevcut olana kadar engellenecektir.
  * [`isready`](@ref) kanalda herhangi bir nesnenin varlığını test ederken, [`wait`](@ref) bir nesnenin kullanılabilir hale gelmesini bekler.
  * Bir [`Channel`](@ref) başlangıçta açık bir durumdadır. Bu, [`take!`](@ref) ve [`put!`](@ref) çağrıları aracılığıyla serbestçe okunup yazılabileceği anlamına gelir. [`close`](@ref), bir `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` kapatır. Kapalı bir `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` üzerinde, `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` başarısız olacaktır. Örneğin:

    ```julia-repl
    julia> c = Channel(2);

    julia> put!(c, 1) # `put!` on an open channel succeeds
    1

    julia> close(c);

    julia> put!(c, 2) # `put!` on a closed channel throws an exception.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```
  * [`take!`](@ref) ve [`fetch`](@ref) (değeri kaldırmadan alır) kapalı bir kanalda mevcut değerleri başarıyla döndürür, ta ki boşalana kadar. Yukarıdaki örneği devam ettirerek:

    ```julia-repl
    julia> fetch(c) # Any number of `fetch` calls succeed.
    1

    julia> fetch(c)
    1

    julia> take!(c) # The first `take!` removes the value.
    1

    julia> take!(c) # No more data available on a closed channel.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```

Basit bir örneği, görevler arası iletişim için kanallar kullanarak düşünelim. Tek bir `jobs` kanalından veri işlemek için 4 görev başlatıyoruz. Görevler, bir kimlik (`job_id`) ile tanımlanan işleri kanala yazar. Bu simülasyondaki her görev bir `job_id` okur, rastgele bir süre bekler ve ardından sonuçlar kanalına `job_id` ve simüle edilen süreden oluşan bir demet yazar. Son olarak, tüm `results` yazdırılır.

```julia-repl
julia> const jobs = Channel{Int}(32);

julia> const results = Channel{Tuple}(32);

julia> function do_work()
           for job_id in jobs
               exec_time = rand()
               sleep(exec_time)                # simulates elapsed time doing actual work
                                               # typically performed externally.
               put!(results, (job_id, exec_time))
           end
       end;

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for i in 1:4 # start 4 tasks to process requests in parallel
           errormonitor(@async do_work())
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds")
           global n = n - 1
       end
4 finished in 0.22 seconds
3 finished in 0.45 seconds
1 finished in 0.5 seconds
7 finished in 0.14 seconds
2 finished in 0.78 seconds
5 finished in 0.9 seconds
9 finished in 0.36 seconds
6 finished in 0.87 seconds
8 finished in 0.79 seconds
10 finished in 0.64 seconds
12 finished in 0.5 seconds
11 finished in 0.97 seconds
0.029772311
```

Bunun yerine `errormonitor(t)` kullanmak yerine, daha sağlam bir çözüm `bind(results, t)` kullanmak olabilir; çünkü bu, beklenmeyen hataları kaydetmekle kalmaz, aynı zamanda ilişkili kaynakların kapanmasını zorlar ve istisnayı her yere yayar.

## More task operations

Görev işlemleri, [`yieldto`](@ref) adlı düşük seviyeli bir ilkeye dayanır. `yieldto(task, value)` mevcut görevi askıya alır, belirtilen `task`'a geçer ve o görevin son `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` çağrısının belirtilen `value` ile dönmesini sağlar. Dikkat edin ki, `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` görev tarzı kontrol akışını kullanmak için gereken tek işlemdir; çağırmak ve dönmek yerine her zaman farklı bir göreve geçiyoruz. Bu nedenle bu özellik "simetrik korutinler" olarak da adlandırılır; her görev aynı mekanizma kullanılarak geçiş yapılır.

[`yieldto`](@ref) güçlüdür, ancak görevlerin çoğu doğrudan onu çağırmaz. Bunun nedenini düşünün. Mevcut görevden ayrılırsanız, muhtemelen bir noktada geri dönmek isteyeceksiniz, ancak geri dönmenin ne zaman gerektiğini bilmek ve geri dönme sorumluluğunu hangi görevin üstlendiğini bilmek önemli bir koordinasyon gerektirebilir. Örneğin, [`put!`](@ref) ve [`take!`](@ref) engelleyici işlemlerdir; bu işlemler, kanallar bağlamında kullanıldığında, tüketicilerin kim olduğunu hatırlamak için durumu korur. Tüketen görevi manuel olarak takip etme gereksiniminin olmaması, `4d61726b646f776e2e436f64652822222c2022707574212229_40726566`'yı düşük seviyeli `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566`'dan daha kolay kullanılabilir hale getirir.

[`yieldto`](@ref) kullanmak için etkili bir şekilde görevleri kullanmak adına birkaç temel işlev daha gereklidir.

  * [`current_task`](@ref) şu anda çalışan göreve bir referans alır.
  * [`istaskdone`](@ref) bir görevin çıkıp çıkmadığını sorgular.
  * [`istaskstarted`](@ref) bir görevin henüz çalışıp çalışmadığını sorgular.
  * [`task_local_storage`](@ref) mevcut göreve özgü bir anahtar-değer deposunu manipüle eder.

## Tasks and events

Çoğu görev geçişi, I/O istekleri gibi olayları beklemek sonucunda gerçekleşir ve Julia Base içinde yer alan bir zamanlayıcı tarafından gerçekleştirilir. Zamanlayıcı, çalıştırılabilir görevlerin bir kuyruğunu tutar ve mesajın gelmesi gibi dış olaylara dayalı olarak görevleri yeniden başlatan bir olay döngüsü yürütür.

The basic function for waiting for an event is [`wait`](@ref). Several objects implement [`wait`](@ref); for example, given a `Process` object, [`wait`](@ref) will wait for it to exit. [`wait`](@ref) is often implicit; for example, a [`wait`](@ref) can happen inside a call to [`read`](@ref) to wait for data to be available.

Tüm bu durumlarda, [`wait`](@ref) nihayetinde [`Condition`](@ref) nesnesi üzerinde çalışır; bu nesne, görevlerin kuyruklanması ve yeniden başlatılmasından sorumludur. Bir görev, `4d61726b646f776e2e436f64652822222c2022776169742229_40726566`'yı `4d61726b646f776e2e436f64652822222c2022436f6e646974696f6e2229_40726566` üzerinde çağırdığında, görev çalıştırılamaz olarak işaretlenir, koşulun kuyruğuna eklenir ve zamanlayıcıya geçer. Zamanlayıcı, çalıştırmak için başka bir görev seçecek veya dış olayları bekleyerek engellenecektir. Her şey yolunda giderse, sonunda bir olay işleyici, koşul üzerinde [`notify`](@ref)'yı çağıracak ve bu, o koşulu bekleyen görevlerin tekrar çalıştırılabilir hale gelmesine neden olacaktır.

[`Task`](@ref) tarafından açıkça oluşturulan bir görev başlangıçta zamanlayıcıya bilinmemektedir. Bu, isterseniz görevleri manuel olarak [`yieldto`](@ref) kullanarak yönetmenizi sağlar. Ancak, böyle bir görev bir olayı beklerken, olay gerçekleştiğinde otomatik olarak yeniden başlatılır, beklediğiniz gibi.
