```
qr(A::SparseMatrixCSC; tol=_default_tol(A), ordering=ORDERING_DEFAULT) -> QRSparse
```

Berechnen Sie die `QR`-Faktorisierung einer spärlichen Matrix `A`. Es werden zeilen- und spaltenreduzierende Permutationen verwendet, sodass `F.R = F.Q'*A[F.prow,F.pcol]`. Die Hauptanwendung dieses Typs besteht darin, kleinste Quadrate oder unterbestimmte Probleme mit [`\`](@ref) zu lösen. Die Funktion ruft die C-Bibliothek SPQR[^ACM933] auf.

!!! Hinweis     `qr(A::SparseMatrixCSC)` verwendet die SPQR-Bibliothek, die Teil von [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) ist. Da diese Bibliothek nur spärliche Matrizen mit [`Float64`](@ref) oder `ComplexF64`-Elementen unterstützt, konvertiert `qr` ab Julia v1.4 `A` in eine Kopie, die vom Typ `SparseMatrixCSC{Float64}` oder `SparseMatrixCSC{ComplexF64}` ist, je nach Bedarf.

# Beispiele

```jldoctest
julia> A = sparse([1,2,3,4], [1,1,2,2], [1.0,1.0,1.0,1.0])
4×2 SparseMatrixCSC{Float64, Int64} mit 4 gespeicherten Einträgen:
 1.0   ⋅
 1.0   ⋅
  ⋅   1.0
  ⋅   1.0

julia> qr(A)
SparseArrays.SPQR.QRSparse{Float64, Int64}
Q-Faktor:
4×4 SparseArrays.SPQR.QRSparseQ{Float64, Int64}
R-Faktor:
2×2 SparseMatrixCSC{Float64, Int64} mit 2 gespeicherten Einträgen:
 -1.41421    ⋅
   ⋅       -1.41421
Zeilenpermutation:
4-element Vector{Int64}:
 1
 3
 4
 2
Spaltenpermutation:
2-element Vector{Int64}:
 1
 2
```

[^ACM933]: Foster, L. V., & Davis, T. A. (2013). Algorithmus 933: Zuverlässige Berechnung des numerischen Rangs, der Nullraum-Basen, der Pseudoinversen Lösungen und der grundlegenden Lösungen unter Verwendung von SuitesparseQR. ACM Trans. Math. Softw., 40(1). [doi:10.1145/2513109.2513116](https://doi.org/10.1145/2513109.2513116)
