```
findmin(itr) -> (x, index)
```

Retourne l'élément minimal de la collection `itr` et son index ou clé. S'il y a plusieurs éléments minimaux, le premier sera retourné. `NaN` est considéré comme inférieur à toutes les autres valeurs sauf `missing`.

Les indices sont du même type que ceux retournés par [`keys(itr)`](@ref) et [`pairs(itr)`](@ref).

Voir aussi : [`findmax`](@ref), [`argmin`](@ref), [`minimum`](@ref).

# Exemples

```jldoctest
julia> findmin([8, 0.1, -9, pi])
(-9.0, 3)

julia> findmin([1, 7, 7, 6])
(1, 1)

julia> findmin([1, 7, 7, NaN])
(NaN, 4)
```
