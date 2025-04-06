```
symdiff(s, itrs...)
```

Konstruiere die symmetrische Differenz der Elemente in den übergebenen Mengen. Wenn `s` kein `AbstractSet` ist, wird die Reihenfolge beibehalten.

Siehe auch [`symdiff!`](@ref), [`setdiff`](@ref), [`union`](@ref) und [`intersect`](@ref).

# Beispiele

```jldoctest
julia> symdiff([1,2,3], [3,4,5], [4,5,6])
3-element Vector{Int64}:
 1
 2
 6

julia> symdiff([1,2,1], [2, 1, 2])
Int64[]
```
