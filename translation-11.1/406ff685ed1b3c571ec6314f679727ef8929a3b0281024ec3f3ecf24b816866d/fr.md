```
CartesianIndex(i, j, k...)   -> I
CartesianIndex((i, j, k...)) -> I
```

Créez un index multidimensionnel `I`, qui peut être utilisé pour indexer un tableau multidimensionnel `A`. En particulier, `A[I]` est équivalent à `A[i,j,k...]`. On peut mélanger librement des indices entiers et des indices `CartesianIndex` ; par exemple, `A[Ipre, i, Ipost]` (où `Ipre` et `Ipost` sont des indices `CartesianIndex` et `i` est un `Int`) peut être une expression utile lors de l'écriture d'algorithmes qui fonctionnent le long d'une seule dimension d'un tableau de dimensionnalité arbitraire.

Un `CartesianIndex` est parfois produit par [`eachindex`](@ref), et toujours lors de l'itération avec des [`CartesianIndices`](@ref) explicites.

Un `I::CartesianIndex` est traité comme un "scalaire" (pas un conteneur) pour `broadcast`. Pour itérer sur les composants d'un `CartesianIndex`, convertissez-le en tuple avec `Tuple(I)`.

# Exemples

```jldoctest
julia> A = reshape(Vector(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[CartesianIndex((1, 1, 1, 1))]
1

julia> A[CartesianIndex((1, 1, 1, 2))]
9

julia> A[CartesianIndex((1, 1, 2, 1))]
5
```

!!! compat "Julia 1.10"
    Utiliser un `CartesianIndex` comme "scalaire" pour `broadcast` nécessite Julia 1.10 ; dans les versions précédentes, utilisez `Ref(I)`.

