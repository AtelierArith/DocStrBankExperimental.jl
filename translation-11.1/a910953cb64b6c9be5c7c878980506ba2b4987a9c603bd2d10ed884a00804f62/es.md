```
rest(iter, state)
```

Un iterador que produce los mismos elementos que `iter`, pero comenzando en el estado dado.

Véase también: [`Iterators.drop`](@ref), [`Iterators.peel`](@ref), [`Base.rest`](@ref).

# Ejemplos

```jldoctest
julia> collect(Iterators.rest([1,2,3,4], 2))
3-element Vector{Int64}:
 2
 3
 4
```
