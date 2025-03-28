```
last(itr, n::Integer)
```

Holen Sie sich die letzten `n` Elemente der iterierbaren Sammlung `itr`, oder weniger Elemente, wenn `itr` nicht lang genug ist.

!!! compat "Julia 1.6"
    Diese Methode erfordert mindestens Julia 1.6.


# Beispiele

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
