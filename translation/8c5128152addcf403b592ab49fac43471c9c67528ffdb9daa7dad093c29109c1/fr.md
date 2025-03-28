```
mapslices(f, A; dims)
```

Transformez les dimensions données du tableau `A` en appliquant une fonction `f` sur chaque tranche de la forme `A[..., :, ..., :, ...]`, avec un deux-points à chaque `d` dans `dims`. Les résultats sont concaténés le long des dimensions restantes.

Par exemple, si `dims = [1,2]` et que `A` est 4-dimensionnel, alors `f` est appelé sur `x = A[:,:,i,j]` pour tous les `i` et `j`, et `f(x)` devient `R[:,:,i,j]` dans le résultat `R`.

Voir aussi [`eachcol`](@ref) ou [`eachslice`](@ref), utilisés avec [`map`](@ref) ou [`stack`](@ref).

# Exemples

```jldoctest
julia> A = reshape(1:30,(2,5,3))
2×5×3 reshape(::UnitRange{Int64}, 2, 5, 3) avec eltype Int64:
[:, :, 1] =
 1  3  5  7   9
 2  4  6  8  10

[:, :, 2] =
 11  13  15  17  19
 12  14  16  18  20

[:, :, 3] =
 21  23  25  27  29
 22  24  26  28  30

julia> f(x::Matrix) = fill(x[1,1], 1,4);  # retourne une matrice 1×4

julia> B = mapslices(f, A, dims=(1,2))
1×4×3 Array{Int64, 3}:
[:, :, 1] =
 1  1  1  1

[:, :, 2] =
 11  11  11  11

[:, :, 3] =
 21  21  21  21

julia> f2(x::AbstractMatrix) = fill(x[1,1], 1,4);

julia> B == stack(f2, eachslice(A, dims=3))
true

julia> g(x) = x[begin] // x[end-1];  # retourne un nombre

julia> mapslices(g, A, dims=[1,3])
1×5×1 Array{Rational{Int64}, 3}:
[:, :, 1] =
 1//21  3//23  1//5  7//27  9//29

julia> map(g, eachslice(A, dims=2))
5-élément Vector{Rational{Int64}}:
 1//21
 3//23
 1//5
 7//27
 9//29

julia> mapslices(sum, A; dims=(1,3)) == sum(A; dims=(1,3))
true
```

Remarquez que dans `eachslice(A; dims=2)`, la dimension spécifiée est celle *sans* deux-points dans la tranche. C'est `view(A,:,i,:)`, tandis que `mapslices(f, A; dims=(1,3))` utilise `A[:,i,:]`. La fonction `f` peut modifier les valeurs dans la tranche sans affecter `A`.
