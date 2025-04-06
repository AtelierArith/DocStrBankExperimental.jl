```
argmin(itr)
```

Renvoie l'index ou la clé de l'élément minimal dans une collection. S'il y a plusieurs éléments minimaux, le premier sera renvoyé.

La collection ne doit pas être vide.

Les indices sont du même type que ceux renvoyés par [`keys(itr)`](@ref) et [`pairs(itr)`](@ref).

`NaN` est considéré comme inférieur à toutes les autres valeurs sauf `missing`.

Voir aussi : [`argmax`](@ref), [`findmin`](@ref).

# Exemples

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
