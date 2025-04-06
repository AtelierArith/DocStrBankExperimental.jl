```
last(itr, n::Integer)
```

Obtiene los últimos `n` elementos de la colección iterable `itr`, o menos elementos si `itr` no es lo suficientemente largo.

!!! compat "Julia 1.6"
    Este método requiere al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> last(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "bar"
 "qux"

julia> last(1:6, 10)
1:6

julia> last(Float64[], 1)
Float64[]
```
