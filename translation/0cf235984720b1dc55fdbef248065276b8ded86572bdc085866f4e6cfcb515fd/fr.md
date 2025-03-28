```
ldlt(A::SparseMatrixCSC; shift = 0.0, check = true, perm=nothing) -> CHOLMOD.Factor
```

Calcule la factorisation $LDL'$ d'une matrice creuse `A`. `A` doit être une [`SparseMatrixCSC`](@ref) ou une vue [`Symmetric`](@ref)/[`Hermitian`](@ref) d'une `SparseMatrixCSC`. Notez que même si `A` n'a pas l'étiquette de type, elle doit toujours être symétrique ou hermitienne. Une permutation réduisant le remplissage est utilisée. `F = ldlt(A)` est le plus souvent utilisé pour résoudre des systèmes d'équations `A*x = b` avec `F\b`. L'objet de factorisation retourné `F` prend également en charge les méthodes [`diag`](@ref), [`det`](@ref), [`logdet`](@ref) et [`inv`](@ref). Vous pouvez extraire des facteurs individuels de `F` en utilisant `F.L`. Cependant, comme le pivotement est activé par défaut, la factorisation est représentée en interne comme `A == P'*L*D*L'*P` avec une matrice de permutation `P` ; utiliser simplement `L` sans tenir compte de `P` donnera des réponses incorrectes. Pour inclure les effets de la permutation, il est généralement préférable d'extraire des facteurs "combinés" comme `PtL = F.PtL` (l'équivalent de `P'*L`) et `LtP = F.UP` (l'équivalent de `L'*P`). La liste complète des facteurs pris en charge est `:L, :PtL, :D, :UP, :U, :LD, :DU, :PtLD, :DUP`.

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

Le paramètre optionnel `shift` calcule la factorisation de `A+shift*I` au lieu de `A`. Si l'argument `perm` est fourni, il doit être une permutation de `1:size(A,1)` donnant l'ordre à utiliser (au lieu de l'ordre AMD par défaut de CHOLMOD).

!!! note
    Cette méthode utilise la bibliothèque CHOLMOD[^ACM887][^DavisHager2009] de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). CHOLMOD ne prend en charge que les types réels ou complexes en simple ou double précision. Les matrices d'entrée qui ne sont pas de ces types d'éléments seront converties en ces types si nécessaire.

    De nombreuses autres fonctions de CHOLMOD sont enveloppées mais ne sont pas exportées du module `Base.SparseArrays.CHOLMOD`.

