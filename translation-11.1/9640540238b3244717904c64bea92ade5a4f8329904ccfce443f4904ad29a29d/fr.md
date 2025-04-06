```
cholesky!(F::CHOLMOD.Factor, A::SparseMatrixCSC; shift = 0.0, check = true) -> CHOLMOD.Factor
```

Calcule la factorisation de Cholesky ($LL'$) de `A`, en réutilisant la factorisation symbolique `F`. `A` doit être une [`SparseMatrixCSC`](@ref) ou une vue [`Symmetric`](@ref)/ [`Hermitian`](@ref) d'une `SparseMatrixCSC`. Notez que même si `A` n'a pas l'étiquette de type, elle doit toujours être symétrique ou hermétique.

Voir aussi [`cholesky`](@ref).

!!! note
    Cette méthode utilise la bibliothèque CHOLMOD de SuiteSparse, qui ne prend en charge que les types réels ou complexes en précision simple ou double. Les matrices d'entrée qui ne sont pas de ces types d'éléments seront converties en ces types si nécessaire.

