```
qr(A::SparseMatrixCSC; tol=_default_tol(A), ordering=ORDERING_DEFAULT) -> QRSparse
```

Calcule la factorisation `QR` d'une matrice creuse `A`. Des permutations de lignes et de colonnes réduisant le remplissage sont utilisées de sorte que `F.R = F.Q'*A[F.prow,F.pcol]`. L'application principale de ce type est de résoudre des problèmes de moindres carrés ou sous-déterminés avec [`\`](@ref). La fonction appelle la bibliothèque C SPQR[^ACM933].

!!! note
    `qr(A::SparseMatrixCSC)` utilise la bibliothèque SPQR qui fait partie de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). Comme cette bibliothèque ne prend en charge que les matrices creuses avec des éléments de type [`Float64`](@ref) ou `ComplexF64`, à partir de Julia v1.4, `qr` convertit `A` en une copie de type `SparseMatrixCSC{Float64}` ou `SparseMatrixCSC{ComplexF64}` selon le cas.


# Exemples

```jldoctest
julia> A = sparse([1,2,3,4], [1,1,2,2], [1.0,1.0,1.0,1.0])
4×2 SparseMatrixCSC{Float64, Int64} avec 4 entrées stockées :
 1.0   ⋅
 1.0   ⋅
  ⋅   1.0
  ⋅   1.0

julia> qr(A)
SparseArrays.SPQR.QRSparse{Float64, Int64}
Facteur Q :
4×4 SparseArrays.SPQR.QRSparseQ{Float64, Int64}
Facteur R :
2×2 SparseMatrixCSC{Float64, Int64} avec 2 entrées stockées :
 -1.41421    ⋅
   ⋅       -1.41421
Permutation de lignes :
Vecteur de 4 éléments Int64 :
 1
 3
 4
 2
Permutation de colonnes :
Vecteur de 2 éléments Int64 :
 1
 2
```

[^ACM933]: Foster, L. V., & Davis, T. A. (2013). Algorithm 933: Reliable Calculation of Numerical Rank, Null Space Bases, Pseudoinverse Solutions, and Basic Solutions Using SuitesparseQR. ACM Trans. Math. Softw., 40(1). [doi:10.1145/2513109.2513116](https://doi.org/10.1145/2513109.2513116)
