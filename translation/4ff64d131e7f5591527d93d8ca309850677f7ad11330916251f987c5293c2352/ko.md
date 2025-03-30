```
ldlt(S::SymTridiagonal) -> LDLt
```

실수 대칭 삼중 대각 행렬 `S`의 `LDLt` (즉, $LDL^T$) 분해를 계산합니다. 여기서 `S = L*Diagonal(d)*L'`이며, `L`은 단위 하삼각 행렬이고 `d`는 벡터입니다. `LDLt` 분해 `F = ldlt(S)`의 주요 용도는 선형 방정식 시스템 `Sx = b`를 `F\b`로 푸는 것입니다.

유사하지만 피벗된 임의의 대칭 또는 에르미트 행렬의 분해에 대한 [`bunchkaufman`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> ldltS = ldlt(S);

julia> b = [6., 7., 8.];

julia> ldltS \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255

julia> S \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255
```
