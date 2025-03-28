```
cholesky(A::SparseMatrixCSC; shift = 0.0, check = true, perm = nothing) -> CHOLMOD.Factor
```

Calcule la factorisation de Cholesky d'une matrice creuse définie positive `A`. `A` doit être une [`SparseMatrixCSC`](@ref) ou une vue [`Symmetric`](@ref)/[`Hermitian`](@ref) d'une `SparseMatrixCSC`. Notez que même si `A` n'a pas l'étiquette de type, elle doit toujours être symétrique ou hermitienne. Si `perm` n'est pas donné, une permutation réduisant le remplissage est utilisée. `F = cholesky(A)` est le plus souvent utilisé pour résoudre des systèmes d'équations avec `F\b`, mais les méthodes [`diag`](@ref), [`det`](@ref) et [`logdet`](@ref) sont également définies pour `F`. Vous pouvez également extraire des facteurs individuels de `F`, en utilisant `F.L`. Cependant, comme le pivotement est activé par défaut, la factorisation est représentée en interne comme `A == P'*L*L'*P` avec une matrice de permutation `P` ; utiliser simplement `L` sans tenir compte de `P` donnera des réponses incorrectes. Pour inclure les effets de la permutation, il est généralement préférable d'extraire des facteurs "combinés" comme `PtL = F.PtL` (l'équivalent de `P'*L`) et `LtP = F.UP` (l'équivalent de `L'*P`).

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

Définir l'argument clé optionnel `shift` calcule la factorisation de `A+shift*I` au lieu de `A`. Si l'argument `perm` est fourni, il doit être une permutation de `1:size(A,1)` donnant l'ordre à utiliser (au lieu de l'ordre AMD par défaut de CHOLMOD).

# Exemples

Dans l'exemple suivant, la permutation réduisant le remplissage utilisée est `[3, 2, 1]`. Si `perm` est défini sur `1:3` pour imposer aucune permutation, le nombre d'éléments non nuls dans le facteur est de 6.

```jldoctest
julia> A = [2 1 1; 1 2 0; 1 0 2]
3×3 Matrix{Int64}:
 2  1  1
 1  2  0
 1  0  2

julia> C = cholesky(sparse(A))
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  5
nnz:     5
success: true

julia> C.p
3-element Vector{Int64}:
 3
 2
 1

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421   0.0       0.0
 0.0       1.41421   0.0
 0.707107  0.707107  1.0

julia> L * L' ≈ A[C.p, C.p]
true

julia> P = sparse(1:3, C.p, ones(3))
3×3 SparseMatrixCSC{Float64, Int64} avec 3 entrées stockées:
  ⋅    ⋅   1.0
  ⋅   1.0   ⋅
 1.0   ⋅    ⋅

julia> P' * L * L' * P ≈ A
true

julia> C = cholesky(sparse(A), perm=1:3)
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  6
nnz:     6
success: true

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421    0.0       0.0
 0.707107   1.22474   0.0
 0.707107  -0.408248  1.1547

julia> L * L' ≈ A
true
```

!!! note
    Cette méthode utilise la bibliothèque CHOLMOD[^ACM887][^DavisHager2009] de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). CHOLMOD ne prend en charge que les types réels ou complexes en simple ou double précision. Les matrices d'entrée qui ne sont pas de ces types d'éléments seront converties en ces types si nécessaire.

    De nombreuses autres fonctions de CHOLMOD sont enveloppées mais non exportées du module `Base.SparseArrays.CHOLMOD`.


[^ACM887]: Chen, Y., Davis, T. A., Hager, W. W., & Rajamanickam, S. (2008). Algorithm 887: CHOLMOD, Supernodal Sparse Cholesky Factorization and Update/Downdate. ACM Trans. Math. Softw., 35(3). [doi:10.1145/1391989.1391995](https://doi.org/10.1145/1391989.1391995)

[^DavisHager2009]: Davis, Timothy A., & Hager, W. W. (2009). Dynamic Supernodes in Sparse Cholesky Update/Downdate and Triangular Solves. ACM Trans. Math. Softw., 35(4). [doi:10.1145/1462173.1462176](https://doi.org/10.1145/1462173.1462176)
