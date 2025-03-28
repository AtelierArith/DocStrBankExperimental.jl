```
rest(iter, state)
```

Ein Iterator, der dieselben Elemente wie `iter` liefert, aber ab dem angegebenen `state` beginnt.

Siehe auch: [`Iterators.drop`](@ref), [`Iterators.peel`](@ref), [`Base.rest`](@ref).

# Beispiele

```jldoctest
julia> collect(Iterators.rest([1,2,3,4], 2))
3-element Vector{Int64}:
 2
 3
 4
```
