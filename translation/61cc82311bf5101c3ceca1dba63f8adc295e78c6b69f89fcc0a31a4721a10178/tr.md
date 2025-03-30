```
Threads.@threads [schedule] for ... end
```

Paralel olarak bir `for` döngüsü çalıştırmak için bir makro. İterasyon alanı, kaba-granüllü görevlere dağıtılır. Bu politika `schedule` argümanı ile belirtilebilir. Döngünün yürütülmesi, tüm iterasyonların değerlendirilmesini bekler.

Ayrıca bakınız: [`@spawn`](@ref Threads.@spawn) ve [`Distributed`](@ref man-distributed) içindeki `pmap`.

# Genişletilmiş yardım

## Anlam

Planlama seçeneği tarafından daha güçlü garantiler belirtilmediği sürece, `@threads` makrosu tarafından yürütülen döngü aşağıdaki anlamlara sahiptir.

`@threads` makrosu döngü gövdesini belirsiz bir sırada ve potansiyel olarak eşzamanlı olarak yürütür. Görevlerin ve işçi iş parçacıklarının kesin atamalarını belirtmez. Atamalar her yürütme için farklı olabilir. Her iterasyon için döngü gövdesi kodu (buna transitif olarak çağrılan herhangi bir kod da dahildir) iterasyonların görevlere dağıtımı veya bunların yürütüldüğü işçi iş parçacığı hakkında herhangi bir varsayımda bulunmamalıdır. Her iterasyon için döngü gövdesi, diğer iterasyonlardan bağımsız olarak ileriye doğru ilerleme yapabilmeli ve veri yarışlarından arınmış olmalıdır. Bu nedenle, iterasyonlar arasında geçersiz senkronizasyonlar kilitlenmelere neden olabilirken, senkronize edilmemiş bellek erişimleri tanımsız davranışa yol açabilir.

Örneğin, yukarıdaki koşullar şunları ima eder:

  * Bir iterasyonda alınan bir kilit *aynı iterasyonda* serbest bırakılmalıdır.
  * `Channel` gibi engelleyici ilkelere dayanarak iterasyonlar arasında iletişim kurmak yanlıştır.
  * Sadece iterasyonlar arasında paylaşılmayan konumlara yazılmalıdır (bir kilit veya atomik işlem kullanılmadıkça).
  * `:static` planlaması kullanılmadıkça, [`threadid()`](@ref Threads.threadid) değeri tek bir iterasyon içinde bile değişebilir. [`Görev Göçü`](@ref man-task-migration) bölümüne bakın.

## Planlayıcılar

Planlayıcı argümanı olmadan, kesin planlama belirtilmemiştir ve Julia sürümleri arasında değişir. Şu anda, planlayıcı belirtilmediğinde `:dynamic` kullanılmaktadır.

!!! uyumluluk "Julia 1.5"
    `schedule` argümanı Julia 1.5 itibarıyla mevcuttur.


### `:dynamic` (varsayılan)

`:dynamic` planlayıcısı, iterasyonları mevcut işçi iş parçacıklarına dinamik olarak yürütür. Mevcut uygulama, her iterasyon için iş yükünün eşit olduğunu varsayar. Ancak, bu varsayım gelecekte kaldırılabilir.

Bu planlama seçeneği, temel yürütme mekanizmasına yalnızca bir ipucudur. Ancak, birkaç özellik beklenebilir. `:dynamic` planlayıcısı tarafından kullanılan `Task` sayısı, mevcut işçi iş parçacıklarının sayısının küçük bir sabit katı ile sınırlıdır ([`Threads.threadpoolsize()`](@ref)). Her görev, iterasyon alanının bitişik bölgelerini işler. Bu nedenle, `@threads :dynamic for x in xs; f(x); end` genellikle `@sync for x in xs; @spawn f(x); end`'den daha verimlidir, eğer `length(xs)` işçi iş parçacıklarının sayısından önemli ölçüde daha büyükse ve `f(x)`'in çalışma süresi, bir görevi başlatma ve senkronize etme maliyetinden (genellikle 10 mikro saniyeden az) nispeten daha küçükse.

!!! uyumluluk "Julia 1.8"
    `schedule` argümanı için `:dynamic` seçeneği mevcut ve varsayılan olarak Julia 1.8 itibarıyla mevcuttur.


### `:greedy`

`:greedy` planlayıcısı, her biri üretilen değerler üzerinde açgözlü bir şekilde çalışan [`Threads.threadpoolsize()`](@ref) kadar görev başlatır. Bir görev işini bitirir bitirmez, iteratörden bir sonraki değeri alır. Herhangi bir bireysel görev tarafından yapılan iş, iteratörden bitişik değerler üzerinde olmayabilir. Verilen iteratör sonsuza kadar değer üretebilir, yalnızca iteratör arayüzü gereklidir (indeksleme yok).

Bu planlama seçeneği, bireysel iterasyonların iş yükü eşit değilse/büyük bir yayılma varsa genellikle iyi bir seçimdir.

!!! uyumluluk "Julia 1.11"
    `schedule` argümanı için `:greedy` seçeneği Julia 1.11 itibarıyla mevcuttur.


### `:static`

`:static` planlayıcısı, her iş parçacığı için bir görev oluşturur ve iterasyonları eşit olarak böler, her görevi belirli bir iş parçacığına atar. Özellikle, [`threadid()`](@ref Threads.threadid) değeri bir iterasyon içinde sabit olacağına dair garanti vardır. Başka bir `@threads` döngüsünden veya 1 dışındaki bir iş parçacığından kullanıldığında `:static` belirtmek bir hatadır.

!!! not
    `:static` planlaması, Julia 1.3'ten önce yazılmış kodun geçişini desteklemek için mevcuttur. Yeni yazılmış kütüphane işlevlerinde, bu seçeneği kullanan işlevlerin rastgele işçi iş parçacıklarından çağrılamayacağı için `:static` planlaması önerilmez.


## Örnekler

Farklı planlama stratejilerini göstermek için, belirli bir süre boyunca çalışan bir zamanlayıcı döngüsü içeren `busywait` fonksiyonunu düşünün.

```julia-repl
julia> function busywait(seconds)
            tstart = time_ns()
            while (time_ns() - tstart) / 1e9 < seconds
            end
        end

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :static for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
6.003001 seconds (16.33 k allocations: 899.255 KiB, 0.25% compilation time)

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :dynamic for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
2.012056 seconds (16.05 k allocations: 883.919 KiB, 0.66% compilation time)
```

`:dynamic` örneği 2 saniye sürer çünkü boşta olan iş parçacıklarından biri, for döngüsünü tamamlamak için iki 1 saniyelik iterasyonu çalıştırabilir. ```
