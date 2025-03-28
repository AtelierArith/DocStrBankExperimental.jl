```
max(x, y, ...)
```

Retourne le maximum des arguments, par rapport à [`isless`](@ref). Si l'un des arguments est [`missing`](@ref), retourne `missing`. Voir aussi la fonction [`maximum`](@ref) pour prendre l'élément maximum d'une collection.

# Exemples

```jldoctest
julia> max(2, 5, 1)
5

julia> max(5, missing, 6)
missing
```
