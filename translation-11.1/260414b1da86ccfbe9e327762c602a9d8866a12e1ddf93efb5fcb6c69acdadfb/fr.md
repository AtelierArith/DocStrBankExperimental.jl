```
cycle(iter[, n::Int])
```

Un itérateur qui parcourt `iter` indéfiniment. Si `n` est spécifié, alors il parcourt `iter` ce nombre de fois. Lorsque `iter` est vide, `cycle(iter)` et `cycle(iter, n)` le sont aussi.

`Iterators.cycle(iter, n)` est l'équivalent paresseux de [`Base.repeat`](@ref)`(vector, n)`, tandis que [`Iterators.repeated`](@ref)`(iter, n)` est le [`Base.fill`](@ref)`(item, n)` paresseux.

!!! compat "Julia 1.11"
    La méthode `cycle(iter, n)` a été ajoutée dans Julia 1.11.


# Exemples

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
