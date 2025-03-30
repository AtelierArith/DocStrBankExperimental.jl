```
schur(A) -> F::Schur
```

행렬 `A`의 슈르 분해를 계산합니다. (준)삼각형 슈르 인자는 `F`라는 `Schur` 객체에서 `F.Schur` 또는 `F.T`를 사용하여 얻을 수 있으며, 직교/유니타리 슈르 벡터는 `F.vectors` 또는 `F.Z`를 사용하여 얻을 수 있습니다. 이때 `A = F.vectors * F.Schur * F.vectors'`가 성립합니다. `A`의 고유값은 `F.values`를 사용하여 얻을 수 있습니다.

실수 `A`의 경우, 슈르 분해는 "준삼각형"이며, 이는 복소수 고유값의 켤레 쌍에 대해 2×2 대각 블록이 있는 상삼각형임을 의미합니다. 이는 복소수 고유값이 있을 때에도 분해가 순수하게 실수일 수 있도록 합니다. 실수 준삼각형 분해에서 (복소수) 순수 상삼각형 슈르 분해를 얻으려면 `Schur{Complex}(schur(A))`를 사용할 수 있습니다.

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
