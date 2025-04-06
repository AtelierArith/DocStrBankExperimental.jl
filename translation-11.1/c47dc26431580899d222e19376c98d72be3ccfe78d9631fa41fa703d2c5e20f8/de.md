```
first(itr, n::Integer)
```

Holen Sie sich die ersten `n` Elemente der iterierbaren Sammlung `itr`, oder weniger Elemente, wenn `itr` nicht lang genug ist.

Siehe auch: [`startswith`](@ref), [`Iterators.take`](@ref).

!!! compat "Julia 1.6"
    Diese Methode erfordert mindestens Julia 1.6.


# Beispiele

```jldoctest
julia> first(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "foo"
 "bar"

julia> first(1:6, 10)
1:6

julia> first(Bool[], 1)
Bool[]
```
