```
checkindex(Bool, inds::AbstractUnitRange, index)
```

Retourne `true` si l'`index` donné est dans les limites de `inds`. Les types personnalisés qui souhaitent se comporter comme des indices pour tous les tableaux peuvent étendre cette méthode afin de fournir une implémentation de vérification des limites spécialisée.

Voir aussi [`checkbounds`](@ref).

# Exemples

```jldoctest
julia> checkindex(Bool, 1:20, 8)
true

julia> checkindex(Bool, 1:20, 21)
false
```
