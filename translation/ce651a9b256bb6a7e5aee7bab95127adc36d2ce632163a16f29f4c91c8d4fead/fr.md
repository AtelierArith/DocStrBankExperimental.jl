```
ldlt!(F::CHOLMOD.Factor, A::SparseMatrixCSC; shift = 0.0, check = true) -> CHOLMOD.Factor
```

Calcule la factorisation $LDL'$ de `A`, en réutilisant la factorisation symbolique `F`. `A` doit être un [`SparseMatrixCSC`](@ref) ou une vue [`Symmetric`](@ref)/[`Hermitian`](@ref) d'un `SparseMatrixCSC`. Notez que même si `A` n'a pas l'étiquette de type, elle doit toujours être symétrique ou hermitienne.

Voir aussi [`ldlt`](@ref).

!!! note
    Cette méthode utilise la bibliothèque CHOLMOD de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse), qui ne prend en charge que les types réels ou complexes en précision simple ou double. Les matrices d'entrée qui ne sont pas de ces types d'éléments seront converties en ces types si nécessaire.

