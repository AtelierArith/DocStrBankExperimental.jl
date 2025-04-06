```
std(itr; corrected::Bool=true, mean=nothing[, dims])
```

Calcule l'écart type de l'échantillon de la collection `itr`.

L'algorithme renvoie un estimateur de l'écart type de la distribution générative sous l'hypothèse que chaque entrée de `itr` est un échantillon tiré de la même distribution inconnue, avec les échantillons non corrélés. Pour les tableaux, ce calcul est équivalent à calculer `sqrt(sum((itr .- mean(itr)).^2) / (length(itr) - 1))`. Si `corrected` est `true`, alors la somme est mise à l'échelle avec `n-1`, tandis que la somme est mise à l'échelle avec `n` si `corrected` est `false`, avec `n` le nombre d'éléments dans `itr`.

Si `itr` est un `AbstractArray`, `dims` peut être fourni pour calculer l'écart type sur les dimensions.

Un `mean` pré-calculé peut être fourni. Lorsque `dims` est spécifié, `mean` doit être un tableau de la même forme que `mean(itr, dims=dims)` (des dimensions singleton supplémentaires à la fin sont autorisées).

!!! note
    Si le tableau contient des valeurs `NaN` ou [`missing`](@ref), le résultat est également `NaN` ou `missing` (`missing` a la priorité si le tableau contient les deux). Utilisez la fonction [`skipmissing`](@ref) pour omettre les entrées `missing` et calculer l'écart type des valeurs non manquantes.

