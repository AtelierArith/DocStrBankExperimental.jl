```
symdiff(s, itrs...)
```

Construit la différence symétrique des éléments dans les ensembles passés. Lorsque `s` n'est pas un `AbstractSet`, l'ordre est maintenu.

Voir aussi [`symdiff!`](@ref), [`setdiff`](@ref), [`union`](@ref) et [`intersect`](@ref).

# Exemples

```jldoctest
julia> symdiff([1,2,3], [3,4,5], [4,5,6])
3-element Vector{Int64}:
 1
 2
 6

julia> symdiff([1,2,1], [2, 1, 2])
Int64[]
```
