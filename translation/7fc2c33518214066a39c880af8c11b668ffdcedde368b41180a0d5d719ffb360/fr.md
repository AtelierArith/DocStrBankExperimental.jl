```
mean(itr)
```

Calculez la moyenne de tous les éléments d'une collection.

!!! note
    Si `itr` contient des valeurs `NaN` ou [`missing`](@ref), le résultat est également `NaN` ou `missing` (`missing` a la priorité si le tableau contient les deux). Utilisez la fonction [`skipmissing`](@ref) pour omettre les entrées `missing` et calculer la moyenne des valeurs non manquantes.


# Exemples

```jldoctest
julia> using Statistics

julia> mean(1:20)
10.5

julia> mean([1, missing, 3])
missing

julia> mean(skipmissing([1, missing, 3]))
2.0
```
