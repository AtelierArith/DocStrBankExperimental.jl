```
cycle(iter[, n::Int])
```

Sonsuz bir şekilde `iter` üzerinden dönen bir iteratördür. Eğer `n` belirtilmişse, o zaman `iter` üzerinden o kadar kez döner. `iter` boş olduğunda, `cycle(iter)` ve `cycle(iter, n)` de boştur.

`Iterators.cycle(iter, n)` [`Base.repeat`](@ref)`(vector, n)`'nin tembel eşdeğeridir, oysa [`Iterators.repeated`](@ref)`(iter, n)` tembel [`Base.fill`](@ref)`(item, n)`'dir.

!!! compat "Julia 1.11"
    `cycle(iter, n)` metodu Julia 1.11'de eklendi.


# Örnekler

```jldoctest
julia> for (i, v) in enumerate(Iterators.cycle("hello"))
           print(v)
           i > 10 && break
       end
hellohelloh

julia> foreach(print, Iterators.cycle(['j', 'u', 'l', 'i', 'a'], 3))
juliajuliajulia

julia> repeat([1,2,3], 4) == collect(Iterators.cycle([1,2,3], 4))
true

julia> fill([1,2,3], 4) == collect(Iterators.repeated([1,2,3], 4))
true
```
