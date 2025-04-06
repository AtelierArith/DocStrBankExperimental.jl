# [Multi-Threading](@id man-multithreading)

Bu [blog post](https://julialang.org/blog/2019/07/multithreading/) adresini ziyaret ederek Julia çoklu iş parçacığı özelliklerinin sunumunu görebilirsiniz.

## Starting Julia with multiple threads

Varsayılan olarak, Julia tek bir yürütme ipliği ile başlar. Bu, [`Threads.nthreads()`](@ref) komutunu kullanarak doğrulanabilir:

```jldoctest
julia> Threads.nthreads()
1
```

İşlem ipliklerinin sayısı, ya `-t`/`--threads` komut satırı argümanı kullanılarak ya da [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) ortam değişkeni kullanılarak kontrol edilir. Her ikisi de belirtildiğinde, `-t`/`--threads` öncelik alır.

İş parçalarının sayısı ya bir tamsayı olarak (`--threads=4`) ya da `auto` olarak (`--threads=auto`) belirtilebilir; burada `auto`, kullanılacak yararlı bir varsayılan iş parçaları sayısını çıkarmaya çalışır (daha fazla bilgi için bkz. [Command-line Options](@ref command-line-interface)).

!!! compat "Julia 1.5"
    `-t`/`--threads` komut satırı argümanı en az Julia 1.5 gerektirir. Daha eski sürümlerde bunun yerine ortam değişkenini kullanmalısınız.


!!! compat "Julia 1.7"
    `auto` değerini [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) ortam değişkeninin değeri olarak kullanmak en az Julia 1.7 gerektirir. Daha eski sürümlerde bu değer göz ardı edilir.


Julia ile 4 iş parçacığı ile başlayalım:

```bash
$ julia --threads 4
```

Dört ipliğin elimizde olduğunu doğrulayalım.

```julia-repl
julia> Threads.nthreads()
4
```

Ama şu anda ana iplikteyiz. Kontrol etmek için [`Threads.threadid`](@ref) fonksiyonunu kullanıyoruz.

```jldoctest
julia> Threads.threadid()
1
```

!!! note
    Eğer ortam değişkenini kullanmayı tercih ediyorsanız, bunu Bash (Linux/macOS) içinde aşağıdaki gibi ayarlayabilirsiniz:

    ```bash
    export JULIA_NUM_THREADS=4
    ```

    C shell üzerinde Linux/macOS, CMD üzerinde Windows:

    ```bash
    set JULIA_NUM_THREADS=4
    ```

    Powershell Windows'ta:

    ```powershell
    $env:JULIA_NUM_THREADS=4
    ```

    Not edin ki bu, Julia'ya başlamadan *önce* yapılmalıdır.


!!! note
    `-t`/`--threads` ile belirtilen iş parçacığı sayısı, `-p`/`--procs` veya `--machine-file` komut satırı seçenekleri kullanılarak oluşturulan işçi süreçlerine aktarılır. Örneğin, `julia -p2 -t2` 2 işçi süreci ile 1 ana süreç oluşturur ve bu üç sürecin de 2 iş parçacığı etkinleştirilmiştir. İşçi iş parçacıkları üzerinde daha ince ayar yapmak için [`addprocs`](@ref) kullanın ve `-t`/`--threads`'i `exeflags` olarak geçirin.


### Multiple GC Threads

Çöp Toplayıcı (GC) birden fazla iş parçacığı kullanabilir. Kullanılan miktar, ya hesaplama işçi iş parçacıklarının sayısının yarısıdır ya da `--gcthreads` komut satırı argümanı veya [`JULIA_NUM_GC_THREADS`](@ref JULIA_NUM_GC_THREADS) ortam değişkeni ile yapılandırılmıştır.

!!! compat "Julia 1.10"
    `--gcthreads` komut satırı argümanı en az Julia 1.10 gerektirir.


## [Threadpools](@id man-threadpools)

Bir programın iş parçacıkları birçok görevle meşgul olduğunda, görevler gecikmeler yaşayabilir ve bu durum programın yanıt verme ve etkileşim yeteneğini olumsuz etkileyebilir. Bunu ele almak için, bir görevin etkileşimli olduğunu belirtebilirsiniz, bunu [`Threads.@spawn`](@ref) ile yapabilirsiniz:

```julia
using Base.Threads
@spawn :interactive f()
```

Etkileşimli görevler yüksek gecikme işlemleri gerçekleştirmekten kaçınmalı ve eğer uzun süreli görevlerse sık sık teslim etmelidir.

Julia, etkileşimli görevleri çalıştırmak için bir veya daha fazla iş parçacığı ayrılmış olarak başlatılabilir:

```bash
$ julia --threads 3,1
```

Ortam değişkeni [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) benzer şekilde de kullanılabilir:

```bash
export JULIA_NUM_THREADS=3,1
```

Bu, `:default` iş havuzunda 3 iş parçacığı ve `:interactive` iş havuzunda 1 iş parçacığı ile Julia'yı başlatır:

```julia-repl
julia> using Base.Threads

julia> nthreadpools()
2

julia> threadpool() # the main thread is in the interactive thread pool
:interactive

julia> nthreads(:default)
3

julia> nthreads(:interactive)
1

julia> nthreads()
3
```

!!! note
    `nthreads`'in sıfır argümanlı versiyonu, varsayılan havuzdaki iş parçacığı sayısını döndürür.


!!! note
    Julia'nın etkileşimli iş parçacıklarıyla başlatılıp başlatılmamasına bağlı olarak, ana iş parçacığı ya varsayılan ya da etkileşimli iş parçacığı havuzundadır.


Her iki veya her iki sayı `auto` kelimesiyle değiştirilebilir, bu da Julia'nın makul bir varsayılan seçmesini sağlar.

## The `@threads` Macro

Basit bir örnek üzerinde çalışalım, yerel iş parçacıklarımızı kullanarak. Sıfırlardan oluşan bir dizi oluşturalım:

```jldoctest
julia> a = zeros(10)
10-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
```

Dört iş parçacığı kullanarak bu dizide aynı anda işlem yapalım. Her iş parçacığı, kendi iş parçacığı kimliğini her konuma yazsın.

Julia, [`Threads.@threads`](@ref) makrosunu kullanarak paralel döngüleri destekler. Bu makro, Julia'ya döngünün çok iş parçacıklı bir alan olduğunu belirtmek için bir `for` döngüsünün önüne eklenir:

```julia-repl
julia> Threads.@threads for i = 1:10
           a[i] = Threads.threadid()
       end
```

İterasyon alanı, iş parçacıkları arasında bölünür; ardından her iş parçacığı, kendi atanan konumlarına iş parçacığı kimliğini yazar:

```julia-repl
julia> a
10-element Vector{Float64}:
 1.0
 1.0
 1.0
 2.0
 2.0
 2.0
 3.0
 3.0
 4.0
 4.0
```

Not edin ki [`Threads.@threads`](@ref) isteğe bağlı bir azaltma parametresine sahip değildir, tıpkı [`@distributed`](@ref) gibi.

### Using `@threads` without data-races

Veri yarışı kavramı ["Communication and data races between threads"](@ref man-communication-and-data-races) içinde detaylandırılmıştır. Şimdilik, bir veri yarışının yanlış sonuçlar ve tehlikeli hatalarla sonuçlanabileceğini bilin.

Diyelim ki `sum_single` fonksiyonunu çok iş parçacıklı hale getirmek istiyoruz.

```julia-repl
julia> function sum_single(a)
           s = 0
           for i in a
               s += i
           end
           s
       end
sum_single (generic function with 1 method)

julia> sum_single(1:1_000_000)
500000500000
```

Sadece `@threads` eklemek, birden fazla iş parçacığının aynı anda `s`'yi okuması ve yazmasıyla bir veri yarışı ortaya çıkarır.

```julia-repl
julia> function sum_multi_bad(a)
           s = 0
           Threads.@threads for i in a
               s += i
           end
           s
       end
sum_multi_bad (generic function with 1 method)

julia> sum_multi_bad(1:1_000_000)
70140554652
```

Sonuç `500000500000` değildir, olması gerektiği gibi ve muhtemelen her değerlendirmede değişecektir.

Bu sorunu çözmek için, göreve özgü tamponlar, toplamı yarışmadan uzak parçalara ayırmak için kullanılabilir. Burada `sum_single`, kendi iç tamponu `s` ile yeniden kullanılır. Giriş vektörü `a`, paralel çalışma için `nthreads()` parçaya bölünür. Ardından, her parçayı ayrı ayrı toplamak için `Threads.@spawn` kullanarak görevler oluştururuz. Son olarak, her görevden gelen sonuçları tekrar `sum_single` ile toplarız:

```julia-repl
julia> function sum_multi_good(a)
           chunks = Iterators.partition(a, length(a) ÷ Threads.nthreads())
           tasks = map(chunks) do chunk
               Threads.@spawn sum_single(chunk)
           end
           chunk_sums = fetch.(tasks)
           return sum_single(chunk_sums)
       end
sum_multi_good (generic function with 1 method)

julia> sum_multi_good(1:1_000_000)
500000500000
```

!!! note
    Tamponlar `threadid()` temelinde yönetilmemelidir, yani `buffers = zeros(Threads.nthreads())` çünkü eşzamanlı görevler yield edebilir, bu da belirli bir iş parçacığında birden fazla eşzamanlı görevin aynı tamponu kullanabileceği anlamına gelir ve veri yarışları riski taşır. Ayrıca, birden fazla iş parçacığı mevcut olduğunda, görevler yield noktalarında iş parçacığını değiştirebilir, bu da [task migration](@ref man-task-migration) olarak bilinir.


Başka bir seçenek, görevler/iş parçaları arasında paylaşılan değişkenler üzerinde atomik işlemlerin kullanılmasıdır; bu, işlemlerin özelliklerine bağlı olarak daha performanslı olabilir.

## [Communication and data-races between threads](@id man-communication-and-data-races)

Julia'nın iş parçacıkları paylaşılan bellek aracılığıyla iletişim kurabilir, ancak doğru ve veri yarışı içermeyen çok iş parçacıklı kod yazmak son derece zordur. Julia'nın [`Channel`](@ref)'ları iş parçacığı güvenlidir ve güvenli bir şekilde iletişim kurmak için kullanılabilir. Ayrıca, veri yarışlarını önlemek için [locks](@ref man-using-locks) ve [atomics](@ref man-atomic-operations) kullanma yöntemlerini açıklayan bölümler de bulunmaktadır.

### Data-race freedom

Programınızın veri yarışı içermediğinden tamamen siz sorumlusunuz ve bu gerekliliği gözlemlemediğiniz takdirde burada verilen hiçbir şey varsayılamaz. Gözlemlenen sonuçlar son derece sezgisel olmayabilir.

Eğer veri yarışları ortaya çıkarsa, Julia bellek güvenli değildir. **Başka bir iş parçacığı bunun üzerine yazabilir, bu nedenle *herhangi bir* veriyi okumada çok dikkatli olun, çünkü bu segmentasyon hatalarına veya daha kötü sonuçlara yol açabilir**. Aşağıda farklı iş parçacıklarından küresel değişkenlere erişmenin birkaç güvensiz yolu bulunmaktadır:

```julia
Thread 1:
global b = false
global a = rand()
global b = true

Thread 2:
while !b; end
bad_read1(a) # it is NOT safe to access `a` here!

Thread 3:
while !@isdefined(a); end
bad_read2(a) # it is NOT safe to access `a` here
```

### [Using locks to avoid data-races](@id man-using-locks)

Veri yarışlarını önlemek ve böylece thread güvenli kod yazmak için önemli bir araç "kilit" kavramıdır. Bir kilit kilitlenebilir ve kilidi açılabilir. Eğer bir thread bir kilidi kilitlediyse ve henüz açmadıysa, bu kilidi "tutuyor" denir. Eğer sadece bir kilit varsa ve bazı verilere erişmek için kilidi tutmayı gerektiren bir kod yazıyorsak, birden fazla thread'in aynı verilere aynı anda erişemeyeceğini garanti edebiliriz. Bir kilit ile bir değişken arasındaki bağlantının programcı tarafından yapıldığını ve program tarafından değil, unutulmamalıdır.

Örneğin, `my_lock` adında bir kilit oluşturabiliriz ve bir değişkeni `my_variable` değiştirirken bu kilidi kullanabiliriz. Bu, en basit şekilde `@lock` makrosu ile yapılır:

```julia-repl
julia> my_lock = ReentrantLock();

julia> my_variable = [1, 2, 3];

julia> @lock my_lock my_variable[1] = 100
100
```

Aynı kilit ve değişkenle benzer bir desen kullanarak, ancak başka bir iş parçacığında, işlemler veri yarışı olmaktan uzaktır.

Yukarıdaki işlemi `lock`'ın fonksiyonel versiyonu ile aşağıdaki iki şekilde gerçekleştirebilirdik:

```julia-repl
julia> lock(my_lock) do
           my_variable[1] = 100
       end
100

julia> begin
           lock(my_lock)
           try
               my_variable[1] = 100
           finally
               unlock(my_lock)
           end
       end
100
```

Tüm üç seçenek eşdeğerdir. Nihai versiyonun, kilidin her zaman açıldığından emin olmak için açık bir `try`-blok gerektirdiğine dikkat edin; oysa ilk iki versiyon bunu dahili olarak yapar. Diğer iş parçacıkları tarafından erişilen verileri (örneğin, global veya closure değişkenine atama yapmak gibi) değiştirirken yukarıdaki kilit desenini her zaman kullanmalısınız. Bunu yapmamak öngörülemeyen ve ciddi sonuçlar doğurabilir.

### [Atomic Operations](@id man-atomic-operations)

Julia, değerleri *atomik* olarak, yani [race conditions](https://en.wikipedia.org/wiki/Race_condition) önlemek için güvenli bir şekilde erişim ve değiştirme desteği sunar. Bir değer (bu değer bir ilkel türde olmalıdır) [`Threads.Atomic`](@ref) şeklinde sarılabilir, bu da bu şekilde erişilmesi gerektiğini belirtir. İşte burada bir örnek görebiliriz:

```julia-repl
julia> i = Threads.Atomic{Int}(0);

julia> ids = zeros(4);

julia> old_is = zeros(4);

julia> Threads.@threads for id in 1:4
           old_is[id] = Threads.atomic_add!(i, id)
           ids[id] = id
       end

julia> old_is
4-element Vector{Float64}:
 0.0
 1.0
 7.0
 3.0

julia> i[]
 10

julia> ids
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

Eğer atomik etiketi kullanmadan toplama işlemini yapmaya çalışsaydık, bir yarış durumu nedeniyle yanlış bir sonuç alabilirdik. Yarışı önlemezsek ne olacağına dair bir örnek:

```julia-repl
julia> using Base.Threads

julia> Threads.nthreads()
4

julia> acc = Ref(0)
Base.RefValue{Int64}(0)

julia> @threads for i in 1:1000
          acc[] += 1
       end

julia> acc[]
926

julia> acc = Atomic{Int64}(0)
Atomic{Int64}(0)

julia> @threads for i in 1:1000
          atomic_add!(acc, 1)
       end

julia> acc[]
1000
```

#### [Per-field atomics](@id man-atomics)

Daha ayrıntılı bir düzeyde atomikleri [`@atomic`](@ref Base.@atomic), [`@atomicswap`](@ref Base.@atomicswap), [`@atomicreplace`](@ref Base.@atomicreplace) makroları ve [`@atomiconce`](@ref Base.@atomiconce) makroları kullanabiliriz.

Bellek modelinin ve tasarımın diğer detaylarının spesifik bilgileri [Julia Atomics Manifesto](https://gist.github.com/vtjnash/11b0031f2e2a66c9c24d33e810b34ec0) adresinde yazılmıştır ve daha sonra resmi olarak yayımlanacaktır.

Herhangi bir alan, bir yapı (struct) bildiriminde `@atomic` ile süslenebilir ve ardından herhangi bir yazma işlemi de `@atomic` ile işaretlenmeli ve tanımlı atomik sıralamalardan birini kullanmalıdır (`:monotonic`, `:acquire`, `:release`, `:acquire_release` veya `:sequentially_consistent`). Atomik bir alanın herhangi bir okuması da bir atomik sıralama kısıtlaması ile anotlanabilir veya belirtilmemişse monotonik (gevşek) sıralama ile yapılacaktır.

!!! compat "Julia 1.7"
    Per-field atomics en az Julia 1.7 gerektirir.


## Side effects and mutable function arguments

Çoklu iş parçacığı kullanırken, [pure](https://en.wikipedia.org/wiki/Pure_function) gibi olmayan fonksiyonları kullanırken dikkatli olmalıyız, çünkü yanlış bir cevap alabiliriz. Örneğin, [name ending with `!`](@ref bang-convention) içeren fonksiyonlar, geleneksel olarak argümanlarını değiştirdiğinden dolayı saf değildir.

## @threadcall

Dış kütüphaneler, [`ccall`](@ref) aracılığıyla çağrılanlar gibi, Julia'nın görev tabanlı G/Ç mekanizması için bir sorun teşkil eder. Eğer bir C kütüphanesi engelleyici bir işlem gerçekleştirirse, bu Julia zamanlayıcısının çağrı geri dönene kadar başka görevleri yürütmesini engeller. (Özel C koduna yapılan ve ardından Julia'ya geri dönen çağrılar istisnadır; bu durumlarda görev bırakılabilir veya `jl_yield()` çağrısı yapan C kodu, [`yield`](@ref)'nın C eşdeğeri olarak kabul edilir.)

[`@threadcall`](@ref) makrosu, böyle bir senaryoda yürütmeyi durdurmaktan kaçınmanın bir yolunu sağlar. Ayrı bir iş parçacığında yürütülmek üzere bir C işlevi planlar. Bunun için varsayılan boyutu 4 olan bir iş parçacığı havuzu kullanılır. İş parçacığı havuzunun boyutu, `UV_THREADPOOL_SIZE` ortam değişkeni aracılığıyla kontrol edilir. Boş bir iş parçacığı beklerken ve bir iş parçacığı mevcut olduğunda işlev yürütülürken, talep eden görev (ana Julia olay döngüsünde) diğer görevlere geçiş yapar. `@threadcall`'ın yürütme tamamlanana kadar geri dönmediğini unutmayın. Kullanıcı bakış açısından, bu nedenle diğer Julia API'leri gibi engelleyici bir çağrıdır.

Çağrılan fonksiyonun Julia'ya geri çağrıda bulunmaması çok önemlidir, çünkü bu durum segfault'a neden olur.

`@threadcall` gelecekteki Julia sürümlerinde kaldırılabilir/değiştirilebilir.

## Caveats

Bu zamanda, Julia çalışma zamanı ve standart kütüphanelerindeki çoğu işlem, kullanıcı kodu veri yarışı içermiyorsa, thread güvenli bir şekilde kullanılabilir. Ancak, bazı alanlarda thread desteğini stabilize etme çalışmaları devam etmektedir. Çoklu iş parçacığı programlamanın birçok doğasında zorlukları vardır ve bir iş parçacığı kullanan program alışılmadık veya istenmeyen bir davranış sergiliyorsa (örneğin, çökme veya gizemli sonuçlar), genellikle önce iş parçacığı etkileşimleri şüphelenilmelidir.

Julia'da iş parçacıklarını kullanırken dikkat edilmesi gereken birkaç özel sınırlama ve uyarı vardır:

  * Temel koleksiyon türleri, en az bir iş parçacığı koleksiyonu değiştirdiğinde birden fazla iş parçacığı tarafından aynı anda kullanılıyorsa manuel kilitleme gerektirir (yaygın örnekler arasında dizilerde `push!` veya bir `Dict`'e öğe eklemek bulunur).
  * [`@spawn`](@ref Threads.@spawn) tarafından kullanılan program, belirsizdir ve güvenilmemelidir.
  * Hesaplama açısından yoğun, bellek ayırmayan görevler, bellek ayıran diğer iş parçacıklarında çöp toplamanın çalışmasını engelleyebilir. Bu durumlarda, GC'nin çalışmasına izin vermek için `GC.safepoint()` çağrısını manuel olarak eklemek gerekebilir. Bu sınırlama gelecekte kaldırılacaktır.
  * Üst düzey işlemleri, örneğin `include` veya `eval` gibi tür, yöntem ve modül tanımlarını paralel olarak çalıştırmaktan kaçının.
  * Kütüphane tarafından kaydedilen sonlandırıcıların, iş parçacıkları etkinleştirildiğinde bozulabileceğini unutmayın. Bu, iş parçacıklarının güvenle yaygın olarak benimsenmeden önce ekosistem genelinde bazı geçiş çalışmalarını gerektirebilir. Daha fazla ayrıntı için [the safe use of finalizers](@ref man-finalizers) bölümüne bakın.

## [Task Migration](@id man-task-migration)

Bir görev belirli bir iş parçacığında çalışmaya başladıktan sonra, görev teslim ederse farklı bir iş parçacığına geçebilir.

Böyle görevler [`@spawn`](@ref Threads.@spawn) veya [`@threads`](@ref Threads.@threads) ile başlatılmış olabilir, ancak `@threads` için `:static` zamanlama seçeneği threadid'yi dondurur.

Bu, çoğu durumda [`threadid()`](@ref Threads.threadid)'ün bir görev içinde sabit olarak ele alınmaması gerektiği ve bu nedenle bir tamponlar veya durum nesneleri vektörüne indekslemek için kullanılmaması gerektiği anlamına gelir.

!!! compat "Julia 1.7"
    Görev göçü, Julia 1.7'de tanıtıldı. Daha önce bu görevler her zaman başlatıldıkları aynı iş parçacığında kalıyordu.


## [Safe use of Finalizers](@id man-finalizers)

Çünkü sonlandırıcılar herhangi bir kodu kesintiye uğratabilir, bu nedenle küresel durumla nasıl etkileşime girecekleri konusunda çok dikkatli olmalılar. Ne yazık ki, sonlandırıcıların kullanılmasının ana nedeni küresel durumu güncellemektir (saf bir fonksiyon genellikle bir sonlandırıcı olarak oldukça anlamsızdır). Bu bizi bir tür ikileme götürüyor. Bu sorunu ele almanın birkaç yaklaşımı vardır:

1. Tek iş parçacıklı olduğunda, kod, kritik bir bölgede sonlandırıcıların planlanmasını önlemek için dahili `jl_gc_enable_finalizers` C fonksiyonunu çağırabilir. Dahili olarak, bu, belirli işlemleri (artımlı paket yükleme, kod üretimi vb.) yaparken özyinelemeyi önlemek için bazı fonksiyonlar (C kilitlerimiz gibi) içinde kullanılır. Bir kilit ve bu bayrağın kombinasyonu, sonlandırıcıları güvenli hale getirmek için kullanılabilir.
2. İkinci bir strateji, Base tarafından birkaç yerde kullanılan, bir sonlandırıcıyı, kilidini özyinelemeli olmayan bir şekilde alabileceği zamana kadar açıkça geciktirmektir. Aşağıdaki örnek, bu stratejinin `Distributed.finalize_ref`'e nasıl uygulanabileceğini göstermektedir:

    ```julia
    function finalize_ref(r::AbstractRemoteRef)
        if r.where > 0 # Check if the finalizer is already run
            if islocked(client_refs) || !trylock(client_refs)
                # delay finalizer for later if we aren't free to acquire the lock
                finalizer(finalize_ref, r)
                return nothing
            end
            try # `lock` should always be followed by `try`
                if r.where > 0 # Must check again here
                    # Do actual cleanup here
                    r.where = 0
                end
            finally
                unlock(client_refs)
            end
        end
        nothing
    end
    ```
3. İlgili üçüncü strateji, yield-free bir kuyruk kullanmaktır. Şu anda Base'te kilitsiz bir kuyruk uygulanmamış olsa da, `Base.IntrusiveLinkedListSynchronized{T}` uygundur. Bu, olay döngüleri ile kod için sıklıkla iyi bir strateji olabilir. Örneğin, bu strateji `Gtk.jl` tarafından yaşam süresi referans sayımı yönetimi için kullanılmaktadır. Bu yaklaşımda, `finalizer` içinde herhangi bir açık iş yapmıyoruz ve bunun yerine daha güvenli bir zamanda çalıştırmak için bir kuyruğa ekliyoruz. Aslında, Julia'nın görev zamanlayıcısı bunu zaten kullanıyor, bu nedenle finalizer'ı `x -> @spawn do_cleanup(x)` olarak tanımlamak bu yaklaşımın bir örneğidir. Ancak, bunun `do_cleanup`'ın hangi iş parçacığında çalıştığını kontrol etmediğini unutmayın, bu nedenle `do_cleanup` hala bir kilit edinmelidir. Kendi kuyruğunuzu uygularsanız, bu doğru olmak zorunda değildir, çünkü o kuyruğu yalnızca kendi iş parçacığınızdan boşaltmayı açıkça yapabilirsiniz.
