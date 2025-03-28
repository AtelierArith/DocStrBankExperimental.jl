```
first(itr, n::Integer)
```

Obtiene los primeros `n` elementos de la colección iterable `itr`, o menos elementos si `itr` no es lo suficientemente largo.

Véase también: [`startswith`](@ref), [`Iterators.take`](@ref).

!!! compat "Julia 1.6"
    Este método requiere al menos Julia 1.6.


# Ejemplos

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
