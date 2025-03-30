```
LDLt <: Factorization
```

실수 [`SymTridiagonal`](@ref) 행렬 `S`의 `LDLt` 분해의 행렬 분해 유형으로, `S = L*Diagonal(d)*L'` 형태입니다. 여기서 `L`은 [`UnitLowerTriangular`](@ref) 행렬이고, `d`는 벡터입니다. `LDLt` 분해 `F = ldlt(S)`의 주요 용도는 선형 방정식 시스템 `Sx = b`를 `F\b`로 푸는 것입니다. 이는 해당 행렬 분해 함수인 [`ldlt`](@ref)의 반환 유형입니다.

분해 `F::LDLt`의 개별 구성 요소는 `getproperty`를 통해 접근할 수 있습니다:

| 구성 요소  | 설명                         |
|:------:|:-------------------------- |
| `F.L`  | `LDLt`의 `L` (단위 하삼각) 부분    |
| `F.D`  | `LDLt`의 `D` (대각선) 부분       |
| `F.Lt` | `LDLt`의 `Lt` (단위 상삼각) 부분   |
| `F.d`  | `D`의 대각선 값들을 포함하는 `Vector` |

# 예제

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> F = ldlt(S)
LDLt{Float64, SymTridiagonal{Float64, Vector{Float64}}}
L factor:
3×3 UnitLowerTriangular{Float64, SymTridiagonal{Float64, Vector{Float64}}}:
 1.0        ⋅         ⋅
 0.333333  1.0        ⋅
 0.0       0.545455  1.0
D factor:
3×3 Diagonal{Float64, Vector{Float64}}:
 3.0   ⋅        ⋅
  ⋅   3.66667   ⋅
  ⋅    ⋅       3.90909
```
