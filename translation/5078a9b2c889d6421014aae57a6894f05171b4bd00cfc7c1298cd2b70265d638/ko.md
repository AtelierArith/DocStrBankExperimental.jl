```
GeneralizedSVD <: Factorization
```

두 행렬 `A`와 `B`의 일반화된 특이값 분해(SVD)의 행렬 분해 유형으로, `A = F.U*F.D1*F.R0*F.Q'` 및 `B = F.V*F.D2*F.R0*F.Q'`입니다. 이는 [`svd(_, _)`](@ref)의 반환 유형으로, 해당 행렬 분해 함수입니다.

M-by-N 행렬 `A`와 P-by-N 행렬 `B`에 대해,

  * `U`는 M-by-M 직교 행렬입니다.
  * `V`는 P-by-P 직교 행렬입니다.
  * `Q`는 N-by-N 직교 행렬입니다.
  * `D1`은 첫 K 항목에 1이 있는 M-by-(K+L) 대각 행렬입니다.
  * `D2`는 상단 오른쪽 L-by-L 블록이 대각선인 P-by-(K+L) 행렬입니다.
  * `R0`는 가장 오른쪽 (K+L)-by-(K+L) 블록이 비특이 상부 블록 삼각형인 (K+L)-by-N 행렬입니다.

`K+L`은 행렬 `[A; B]`의 유효 수치적 계수입니다.

분해를 반복하면 구성 요소 `U`, `V`, `Q`, `D1`, `D2`, 및 `R0`가 생성됩니다.

`F.D1`과 `F.D2`의 항목은 관련이 있으며, 이는 [일반화된 SVD](https://www.netlib.org/lapack/lug/node36.html) 및 그 아래에서 호출되는 [xGGSVD3](https://www.netlib.org/lapack/explore-html/d6/db3/dggsvd3_8f.html) 루틴에 대한 LAPACK 문서에서 설명되어 있습니다( LAPACK 3.6.0 및 이후 버전).

# 예제

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> F = svd(A, B)
GeneralizedSVD{Float64, Matrix{Float64}, Float64, Vector{Float64}}
U factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
V factor:
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0   0.0
Q factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
D1 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
D2 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
R0 factor:
2×2 Matrix{Float64}:
 1.41421   0.0
 0.0      -1.41421

julia> F.U*F.D1*F.R0*F.Q'
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> F.V*F.D2*F.R0*F.Q'
2×2 Matrix{Float64}:
 -0.0  1.0
  1.0  0.0
```
