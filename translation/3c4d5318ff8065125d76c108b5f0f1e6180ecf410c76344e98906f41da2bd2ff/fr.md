```
argmax(itr)
```

Retourne l'index ou la clé de l'élément maximal dans une collection. S'il y a plusieurs éléments maximaux, le premier sera retourné.

La collection ne doit pas être vide.

Les indices sont du même type que ceux retournés par [`keys(itr)`](@ref) et [`pairs(itr)`](@ref).

Les valeurs sont comparées avec `isless`.

Voir aussi : [`argmin`](@ref), [`findmax`](@ref).

# Exemples

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
