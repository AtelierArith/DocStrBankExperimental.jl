```
findmax(itr) -> (x, index)
```

Retourne l'élément maximal de la collection `itr` et son index ou clé. S'il y a plusieurs éléments maximaux, le premier sera retourné. Les valeurs sont comparées avec `isless`.

Les indices sont du même type que ceux retournés par [`keys(itr)`](@ref) et [`pairs(itr)`](@ref).

Voir aussi : [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref).

# Exemples

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
