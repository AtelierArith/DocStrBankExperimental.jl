```
@task
```

Bir ifadeyi çalıştırmadan [`Task`](@ref) içine sarın ve [`Task`](@ref) döndürün. Bu yalnızca bir görev oluşturur ve çalıştırmaz.

!!! warning
    Varsayılan olarak görevlerin yapışkan bitinin `true` olarak ayarlanmış olacaktır `t.sticky`. Bu, [`@async`](@ref) için tarihsel varsayılanı modellemektedir. Yapışkan görevler yalnızca ilk olarak planlandıkları işçi iş parçacığında çalıştırılabilir ve planlandıklarında, planlandıkları görev yapışkan hale gelecektir. [`Threads.@spawn`](@ref) davranışını elde etmek için yapışkan bitini manuel olarak `false` olarak ayarlayın.


# Örnekler

```jldoctest
julia> a1() = sum(i for i in 1:1000);

julia> b = @task a1();

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
