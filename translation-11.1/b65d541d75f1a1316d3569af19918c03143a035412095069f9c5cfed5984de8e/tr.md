```
Channel{T=Any}(func::Function, size=0; taskref=nothing, spawn=false, threadpool=nothing)
```

`func`'dan yeni bir görev oluşturun, bunu `T` türünde ve `size` boyutunda yeni bir kanala bağlayın ve görevi, hepsini tek bir çağrıda planlayın. Görev sona erdiğinde kanal otomatik olarak kapatılır.

`func`, bağlı kanalı tek argümanı olarak kabul etmelidir.

Oluşturulan göreve bir referansa ihtiyacınız varsa, anahtar argüman `taskref` aracılığıyla bir `Ref{Task}` nesnesi geçirin.

Eğer `spawn=true` ise, `func` için oluşturulan `Task`, paralel olarak başka bir iş parçacığında planlanabilir; bu, bir görevi [`Threads.@spawn`](@ref) aracılığıyla oluşturmakla eşdeğerdir.

Eğer `spawn=true` ve `threadpool` argümanı ayarlanmamışsa, varsayılan olarak `:default` olur.

Eğer `threadpool` argmanı ayarlanmışsa (`:default` veya `:interactive` olarak), bu `spawn=true` anlamına gelir ve yeni Görev belirtilen iş parçacığı havuzuna oluşturulur.

Bir `Channel` döndürün.

# Örnekler

```jldoctest
julia> chnl = Channel() do ch
           foreach(i -> put!(ch, i), 1:4)
       end;

julia> typeof(chnl)
Channel{Any}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

Oluşturulan görevi referans alma:

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = Channel(taskref=taskref) do ch
           println(take!(ch))
       end;

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
Hello

julia> istaskdone(taskref[])
true
```

!!! compat "Julia 1.3"
    `spawn=` parametresi Julia 1.3'te eklendi. Bu yapıcı Julia 1.3'te eklendi. Daha önceki Julia sürümlerinde, Channel `size` ve `T`'yi ayarlamak için anahtar argümanlar kullanıyordu, ancak bu yapıcılar kullanımdan kaldırılmıştır.


!!! compat "Julia 1.9"
    `threadpool=` argümanı Julia 1.9'da eklendi.


```jldoctest
julia> chnl = Channel{Char}(1, spawn=true) do ch
           for c in "hello world"
               put!(ch, c)
           end
       end
Channel{Char}(1) (2 items available)

julia> String(collect(chnl))
"hello world"
```
