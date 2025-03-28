```
cycle(iter[, n::Int])
```

Un iterador que cicla a través de `iter` para siempre. Si se especifica `n`, entonces cicla a través de `iter` tantas veces. Cuando `iter` está vacío, también lo están `cycle(iter)` y `cycle(iter, n)`.

`Iterators.cycle(iter, n)` es el equivalente perezoso de [`Base.repeat`](@ref)`(vector, n)`, mientras que [`Iterators.repeated`](@ref)`(iter, n)` es el perezoso [`Base.fill`](@ref)`(item, n)`.

!!! compat "Julia 1.11"
    El método `cycle(iter, n)` se agregó en Julia 1.11.


# Ejemplos

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
