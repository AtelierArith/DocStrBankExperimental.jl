```
permute!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti},
         p::AbstractVector{<:Integer}, q::AbstractVector{<:Integer},
         [C::AbstractSparseMatrixCSC{Tv,Ti}]) where {Tv,Ti}
```

Permute bilatéralement `A`, en stockant le résultat `PAQ` (`A[p,q]`) dans `X`. Stocke le résultat intermédiaire `(AQ)^T` (`transpose(A[:,q])`) dans l'argument optionnel `C` s'il est présent. Nécessite qu'aucun de `X`, `A`, et, si présent, `C` ne s'aliasent ; pour stocker le résultat `PAQ` de nouveau dans `A`, utilisez la méthode suivante sans `X` :

```
permute!(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
         q::AbstractVector{<:Integer}[, C::AbstractSparseMatrixCSC{Tv,Ti},
         [workcolptr::Vector{Ti}]]) where {Tv,Ti}
```

Les dimensions de `X` doivent correspondre à celles de `A` (`size(X, 1) == size(A, 1)` et `size(X, 2) == size(A, 2)`), et `X` doit avoir suffisamment de stockage pour accueillir toutes les entrées allouées dans `A` (`length(rowvals(X)) >= nnz(A)` et `length(nonzeros(X)) >= nnz(A)`). La longueur de la permutation de colonne `q` doit correspondre au nombre de colonnes de `A` (`length(q) == size(A, 2)`). La longueur de la permutation de ligne `p` doit correspondre au nombre de lignes de `A` (`length(p) == size(A, 1)`).

Les dimensions de `C` doivent correspondre à celles de `transpose(A)` (`size(C, 1) == size(A, 2)` et `size(C, 2) == size(A, 1)`), et `C` doit avoir suffisamment de stockage pour accueillir toutes les entrées allouées dans `A` (`length(rowvals(C)) >= nnz(A)` et `length(nonzeros(C)) >= nnz(A)`).

Pour des informations supplémentaires (algorithmique), et pour des versions de ces méthodes qui se passent de vérification des arguments, voir les méthodes parentes (non exportées) `unchecked_noalias_permute!` et `unchecked_aliasing_permute!`.

Voir aussi [`permute`](@ref).
