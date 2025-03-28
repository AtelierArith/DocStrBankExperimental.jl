```
min(x, y, ...)
```

Retourne le minimum des arguments, par rapport à [`isless`](@ref). Si l'un des arguments est [`missing`](@ref), retourne `missing`. Voir aussi la fonction [`minimum`](@ref) pour prendre l'élément minimum d'une collection.

# Exemples

```jldoctest
julia> min(2, 5, 1)
1

julia> min(4, missing, 6)
missing
```
