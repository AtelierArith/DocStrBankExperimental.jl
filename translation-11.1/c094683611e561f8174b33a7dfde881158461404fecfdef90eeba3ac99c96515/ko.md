```
lq(A) -> S::LQ
```

`A`의 LQ 분해를 계산합니다. 분해의 하삼각형 구성 요소는 [`LQ`](@ref) 객체 `S`에서 `S.L`을 통해 얻을 수 있으며, 직교/유니타리 구성 요소는 `S.Q`를 통해 얻을 수 있습니다. 따라서 `A ≈ S.L*S.Q`입니다.

분해를 반복하면 구성 요소 `S.L`과 `S.Q`를 생성합니다.

LQ 분해는 `transpose(A)`의 QR 분해이며, 이는 과소정의 방정식 시스템에 대한 최소 노름 해 `lq(A) \ b`를 계산하는 데 유용합니다(`A`는 열이 행보다 많지만 전체 행 랭크를 가집니다).

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
