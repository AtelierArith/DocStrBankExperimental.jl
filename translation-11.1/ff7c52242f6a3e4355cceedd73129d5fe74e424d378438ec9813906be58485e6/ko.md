```
LQ <: Factorization
```

행렬 `A`의 `LQ` 분해의 행렬 분해 유형입니다. `LQ` 분해는 `transpose(A)`의 [`QR`](@ref) 분해입니다. 이는 해당 행렬 분해 함수인 [`lq`](@ref)의 반환 유형입니다.

`S::LQ`가 분해 객체인 경우, 하삼각 성분은 `S.L`을 통해 얻을 수 있으며, 직교/단위 성분은 `S.Q`를 통해 얻을 수 있습니다. 따라서 `A ≈ S.L*S.Q`입니다.

분해를 반복하면 성분 `S.L`과 `S.Q`를 생성합니다.

# 예제

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L factor:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q factor: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # 반복을 통한 구조 분해

julia> l == S.L &&  q == S.Q
true
```
