```
cycle(iter[, n::Int])
```

Ein Iterator, der durch `iter` für immer zirkuliert. Wenn `n` angegeben ist, zirkuliert er durch `iter` so oft. Wenn `iter` leer ist, sind auch `cycle(iter)` und `cycle(iter, n)` leer.

`Iterators.cycle(iter, n)` ist das faule Äquivalent von [`Base.repeat`](@ref)`(vector, n)`, während [`Iterators.repeated`](@ref)`(iter, n)` das faule [`Base.fill`](@ref)`(item, n)` ist.

!!! compat "Julia 1.11"
    Die Methode `cycle(iter, n)` wurde in Julia 1.11 hinzugefügt.


# Beispiele

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
