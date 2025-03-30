```
schedule(t::Task, [val]; error=false)
```

Bir [`Task`](@ref) zamanlayıcının kuyruğuna eklenir. Bu, sistem başka bir şey yapmadığında görevin sürekli çalışmasını sağlar, ancak görev [`wait`](@ref) gibi bir engelleyici işlem yapıyorsa bu durum geçerli değildir.

İkinci bir argüman `val` sağlanırsa, bu değer görev tekrar çalıştığında ([`yieldto`](@ref) aracılığıyla) göreve iletilecektir. Eğer `error` `true` ise, değer uyanan görevde bir istisna olarak yükseltilir.

!!! uyarı     Zaten başlatılmış bir `Task` üzerinde `schedule` kullanmak yanlıştır. Daha fazla bilgi için [API referansına](@ref low-level-schedule-wait) bakın.

!!! uyarı     Varsayılan olarak görevlerin yapışkan bitinin `true` olarak ayarlandığı `t.sticky` olacaktır. Bu, [`@async`](@ref) için tarihsel varsayılanı modellemektedir. Yapışkan görevler yalnızca ilk olarak planlandıkları işçi iş parçacığında çalıştırılabilir ve planlandıklarında, planlandıkları görev yapışkan hale gelecektir. [`Threads.@spawn`](@ref) davranışını elde etmek için yapışkan bitini manuel olarak `false` olarak ayarlayın.

# Örnekler

```jldoctest
julia> a5() = sum(i for i in 1:1000);

julia> b = Task(a5);

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskstarted(b)
true

julia> istaskdone(b)
true
```
