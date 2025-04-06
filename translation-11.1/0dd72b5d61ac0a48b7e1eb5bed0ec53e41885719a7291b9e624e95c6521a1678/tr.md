```
Threads.foreach(f, channel::Channel;
                schedule::Threads.AbstractSchedule=Threads.FairSchedule(),
                ntasks=Threads.threadpoolsize())
```

`foreach(f, channel)` ile benzer, ancak `channel` üzerinde yineleme ve `f`'ye yapılan çağrılar, `Threads.@spawn` tarafından başlatılan `ntasks` görevine dağıtılır. Bu fonksiyon, tüm dahili olarak başlatılan görevlerin tamamlanmasını bekleyecektir.

Eğer `schedule isa FairSchedule` ise, `Threads.foreach` görevleri, Julia'nın zamanlayıcısının iş öğelerini daha serbest bir şekilde iş parçacıkları arasında yük dengelemesi yapabilmesi için başlatmaya çalışacaktır. Bu yaklaşım genellikle her bir öğe için daha yüksek bir yükleme süresine sahiptir, ancak diğer çok iş parçacıklı iş yükleri ile birlikte `StaticSchedule`'dan daha iyi performans gösterebilir.

Eğer `schedule isa StaticSchedule` ise, `Threads.foreach` görevleri, `FairSchedule`'dan daha düşük bir her bir öğe için yükleme süresi ile başlatacaktır, ancak yük dengelemesine daha az uygundur. Bu yaklaşım, ince taneli, homojen iş yükleri için daha uygun olabilir, ancak diğer çok iş parçacıklı iş yükleri ile birlikte `FairSchedule`'dan daha kötü performans gösterebilir.

# Örnekler

```julia-repl
julia> n = 20

julia> c = Channel{Int}(ch -> foreach(i -> put!(ch, i), 1:n), 1)

julia> d = Channel{Int}(n) do ch
           f = i -> put!(ch, i^2)
           Threads.foreach(f, c)
       end

julia> collect(d)
collect(d) = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

!!! uyumluluk "Julia 1.6"
    Bu fonksiyon Julia 1.6 veya daha yenisini gerektirir.

