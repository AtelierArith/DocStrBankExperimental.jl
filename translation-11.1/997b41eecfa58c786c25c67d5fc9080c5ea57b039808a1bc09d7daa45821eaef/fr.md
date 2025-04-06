```
setdiff(s, itrs...)
```

Construit l'ensemble des éléments dans `s` mais pas dans aucun des itérables dans `itrs`. Maintient l'ordre avec des tableaux.

Voir aussi [`setdiff!`](@ref), [`union`](@ref) et [`intersect`](@ref).

# Exemples

```jldoctest
julia> setdiff([1,2,3], [3,4,5])
2-element Vector{Int64}:
 1
 2
```
