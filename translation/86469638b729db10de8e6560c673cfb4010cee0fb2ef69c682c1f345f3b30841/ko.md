```
qr(A::SparseMatrixCSC; tol=_default_tol(A), ordering=ORDERING_DEFAULT) -> QRSparse
```

희소 행렬 `A`의 `QR` 분해를 계산합니다. `F.R = F.Q'*A[F.prow,F.pcol]`가 되도록 행과 열의 채우기 감소 순열이 사용됩니다. 이 유형의 주요 응용 프로그램은 [`\`](@ref)를 사용하여 최소 제곱 또는 미결정 문제를 해결하는 것입니다. 이 함수는 C 라이브러리 SPQR[^ACM933]를 호출합니다.

!!! note
    `qr(A::SparseMatrixCSC)`는 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse)의 일부인 SPQR 라이브러리를 사용합니다. 이 라이브러리는 [`Float64`](@ref) 또는 `ComplexF64` 요소를 가진 희소 행렬만 지원하므로, Julia v1.4부터 `qr`는 `A`를 `SparseMatrixCSC{Float64}` 또는 `SparseMatrixCSC{ComplexF64}` 유형의 복사본으로 변환합니다.


# 예제

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
