```
qr(A::SparseMatrixCSC; tol=_default_tol(A), ordering=ORDERING_DEFAULT) -> QRSparse
```

计算稀疏矩阵 `A` 的 `QR` 分解。使用填充减少的行和列置换，使得 `F.R = F.Q'*A[F.prow,F.pcol]`。这种类型的主要应用是解决最小二乘或欠定问题，使用 [`\`](@ref)。该函数调用 C 库 SPQR[^ACM933]。

!!! note
    `qr(A::SparseMatrixCSC)` 使用的是 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) 中的 SPQR 库。由于该库仅支持具有 [`Float64`](@ref) 或 `ComplexF64` 元素的稀疏矩阵，因此从 Julia v1.4 开始，`qr` 将 `A` 转换为适当类型的 `SparseMatrixCSC{Float64}` 或 `SparseMatrixCSC{ComplexF64}` 的副本。


# 示例

```jldoctest
julia> A = sparse([1,2,3,4], [1,1,2,2], [1.0,1.0,1.0,1.0])
4×2 SparseMatrixCSC{Float64, Int64} with 4 stored entries:
 1.0   ⋅
 1.0   ⋅
  ⋅   1.0
  ⋅   1.0

julia> qr(A)
SparseArrays.SPQR.QRSparse{Float64, Int64}
Q factor:
4×4 SparseArrays.SPQR.QRSparseQ{Float64, Int64}
R factor:
2×2 SparseMatrixCSC{Float64, Int64} with 2 stored entries:
 -1.41421    ⋅
   ⋅       -1.41421
Row permutation:
4-element Vector{Int64}:
 1
 3
 4
 2
Column permutation:
2-element Vector{Int64}:
 1
 2
```

[^ACM933]: Foster, L. V., & Davis, T. A. (2013). Algorithm 933: Reliable Calculation of Numerical Rank, Null Space Bases, Pseudoinverse Solutions, and Basic Solutions Using SuitesparseQR. ACM Trans. Math. Softw., 40(1). [doi:10.1145/2513109.2513116](https://doi.org/10.1145/2513109.2513116)
