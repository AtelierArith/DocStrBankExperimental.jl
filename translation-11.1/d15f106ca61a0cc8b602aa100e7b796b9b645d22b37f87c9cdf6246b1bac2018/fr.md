```
dot(x, A, y)
```

Calcule le produit scalaire généralisé `dot(x, A*y)` entre deux vecteurs `x` et `y`, sans stocker le résultat intermédiaire de `A*y`. Comme pour la fonction à deux arguments [`dot(_,_)`](@ref), cela agit de manière récursive. De plus, pour les vecteurs complexes, le premier vecteur est conjugué.

!!! compat "Julia 1.4"
    La fonction `dot` à trois arguments nécessite au moins Julia 1.4.


# Exemples

```jldoctest
julia> dot([1; 1], [1 2; 3 4], [2; 3])
26

julia> dot(1:5, reshape(1:25, 5, 5), 2:6)
4850

julia> ⋅(1:5, reshape(1:25, 5, 5), 2:6) == dot(1:5, reshape(1:25, 5, 5), 2:6)
true
```
