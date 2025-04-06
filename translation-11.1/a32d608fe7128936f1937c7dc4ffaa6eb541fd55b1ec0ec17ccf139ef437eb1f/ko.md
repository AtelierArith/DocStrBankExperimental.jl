```
Schur <: Factorization
```

행렬 `A`의 슈르 분해의 행렬 분해 유형입니다. 이는 [`schur(_)`](@ref)와 해당하는 행렬 분해 함수의 반환 유형입니다.

`F::Schur`가 분해 객체인 경우, (준)삼각형 슈르 인자는 `F.Schur` 또는 `F.T`를 통해 얻을 수 있으며, 직교/유니타리 슈르 벡터는 `F.vectors` 또는 `F.Z`를 통해 얻을 수 있습니다. 따라서 `A = F.vectors * F.Schur * F.vectors'`입니다. `A`의 고유값은 `F.values`로 얻을 수 있습니다.

분해를 반복하면 구성 요소 `F.T`, `F.Z`, 및 `F.values`가 생성됩니다.

# 예제

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T 인자:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z 인자:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
고유값:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # 반복을 통한 구조 분해

julia> t == F.T && z == F.Z && vals == F.values
true
```
