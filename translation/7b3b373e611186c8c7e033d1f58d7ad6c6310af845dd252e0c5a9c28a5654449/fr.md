```
halfperm!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{TvA,Ti},
          q::AbstractVector{<:Integer}, f::Function = identity) where {Tv,TvA,Ti}
```

Permute par colonne et transpose `A`, en appliquant simultanément `f` à chaque entrée de `A`, en stockant le résultat `(f(A)Q)^T` (`map(f, transpose(A[:,q]))`) dans `X`.

Le type d'élément `Tv` de `X` doit correspondre à `f(::TvA)`, où `TvA` est le type d'élément de `A`. Les dimensions de `X` doivent correspondre à celles de `transpose(A)` (`size(X, 1) == size(A, 2)` et `size(X, 2) == size(A, 1)`), et `X` doit avoir suffisamment de stockage pour accueillir toutes les entrées allouées dans `A` (`length(rowvals(X)) >= nnz(A)` et `length(nonzeros(X)) >= nnz(A)`). La longueur de la permutation par colonne `q` doit correspondre au nombre de colonnes de `A` (`length(q) == size(A, 2)`).

Cette méthode est la méthode parente de plusieurs méthodes effectuant des opérations de transposition et de permutation sur [`SparseMatrixCSC`](@ref)s. Comme cette méthode ne vérifie pas les arguments, il est préférable d'utiliser les méthodes enfants plus sûres (`[c]transpose[!]`, `permute[!]`) plutôt que d'utiliser directement celle-ci.

Cette méthode implémente l'algorithme `HALFPERM` décrit dans F. Gustavson, "Two fast algorithms for sparse matrices: multiplication and permuted transposition," ACM TOMS 4(3), 250-269 (1978). L'algorithme s'exécute en temps `O(size(A, 1), size(A, 2), nnz(A))` et ne nécessite pas d'espace au-delà de celui passé en entrée.
