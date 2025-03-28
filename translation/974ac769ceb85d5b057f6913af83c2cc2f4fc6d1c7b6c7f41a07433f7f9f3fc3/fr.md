```
median(itr)
```

Calculez la médiane de tous les éléments d'une collection. Pour un nombre pair d'éléments, il n'existe pas d'élément médian exact, donc le résultat équivaut à calculer la moyenne de deux éléments médians.

!!! note
    Si `itr` contient des valeurs `NaN` ou [`missing`](@ref), le résultat est également `NaN` ou `missing` (`missing` a la priorité si `itr` contient les deux). Utilisez la fonction [`skipmissing`](@ref) pour omettre les entrées `missing` et calculer la médiane des valeurs non manquantes.


# Exemples

```jldoctest
julia> using Statistics

julia> median([1, 2, 3])
2.0

julia> median([1, 2, 3, 4])
2.5

julia> median([1, 2, missing, 4])
missing

julia> median(skipmissing([1, 2, missing, 4]))
2.0
```
