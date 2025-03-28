```
setdiff(s, itrs...)
```

Konstruiere die Menge der Elemente in `s`, die jedoch nicht in einem der Iterierbaren in `itrs` enthalten sind. Behalte die Reihenfolge mit Arrays bei.

Siehe auch [`setdiff!`](@ref), [`union`](@ref) und [`intersect`](@ref).

# Beispiele

```jldoctest
julia> setdiff([1,2,3], [3,4,5])
2-element Vector{Int64}:
 1
 2
```
