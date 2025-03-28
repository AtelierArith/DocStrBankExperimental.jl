```
cumsum(itr)
```

Somme cumulative d'un itérateur.

Voir aussi [`accumulate`](@ref) pour appliquer des fonctions autres que `+`.

!!! compat "Julia 1.5"
    `cumsum` sur un itérateur non tableau nécessite au moins Julia 1.5.


# Exemples

```jldoctest
julia> cumsum(1:3)
3-element Vector{Int64}:
 1
 3
 6

julia> cumsum((true, false, true, false, true))
(1, 1, 2, 2, 3)

julia> cumsum(fill(1, 2) for i in 1:3)
3-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]
 [3, 3]
```
