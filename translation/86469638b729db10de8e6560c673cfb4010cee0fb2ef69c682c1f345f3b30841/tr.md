```
qr(A::SparseMatrixCSC; tol=_default_tol(A), ordering=ORDERING_DEFAULT) -> QRSparse
```

Seyrek bir matris `A`'nın `QR` faktorizasyonunu hesaplar. `F.R = F.Q'*A[F.prow,F.pcol]` olacak şekilde dolgu azaltıcı satır ve sütun permütasyonları kullanılır. Bu türün ana uygulaması, [`\`](@ref) ile en küçük kareler veya yetersiz problemleri çözmektir. Fonksiyon, C kütüphanesi SPQR'yi çağırır[^ACM933].

!!! note
    `qr(A::SparseMatrixCSC)` [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) parçası olan SPQR kütüphanesini kullanır. Bu kütüphane yalnızca [`Float64`](@ref) veya `ComplexF64` elemanlarına sahip seyrek matrisleri desteklediğinden, Julia v1.4 itibarıyla `qr`, `A`'yı uygun şekilde `SparseMatrixCSC{Float64}` veya `SparseMatrixCSC{ComplexF64}` türünde bir kopyaya dönüştürür.


# Örnekler

```jldoctest
julia> A = sparse([1,2,3,4], [1,1,2,2], [1.0,1.0,1.0,1.0])
4×2 SparseMatrixCSC{Float64, Int64} with 4 stored entries:
 1.0   ⋅
 1.0   ⋅
  ⋅   1.0
  ⋅   1.0

julia> qr(A)
SparseArrays.SPQR.QRSparse{Float64, Int64}
Q faktörü:
4×4 SparseArrays.SPQR.QRSparseQ{Float64, Int64}
R faktörü:
2×2 SparseMatrixCSC{Float64, Int64} with 2 stored entries:
 -1.41421    ⋅
   ⋅       -1.41421
Satır permütasyonu:
4 elemanlı Vector{Int64}:
 1
 3
 4
 2
Sütun permütasyonu:
2 elemanlı Vector{Int64}:
 1
 2
```

[^ACM933]: Foster, L. V., & Davis, T. A. (2013). Algoritma 933: Sayısal Sıra, Null Alan Temelleri, Pseudoinverse Çözümleri ve SuiteSparseQR Kullanarak Temel Çözümlerinin Güvenilir Hesaplanması. ACM Trans. Math. Softw., 40(1). [doi:10.1145/2513109.2513116](https://doi.org/10.1145/2513109.2513116)
