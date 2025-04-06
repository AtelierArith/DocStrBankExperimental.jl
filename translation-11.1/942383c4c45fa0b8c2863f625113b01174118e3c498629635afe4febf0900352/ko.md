```
LU <: Factorization
```

정방 행렬 `A`의 `LU` 분해의 행렬 분해 유형입니다. 이는 해당 행렬 분해 함수인 [`lu`](@ref)의 반환 유형입니다.

분해 `F::LU`의 개별 구성 요소는 [`getproperty`](@ref)를 통해 접근할 수 있습니다:

| 구성 요소 | 설명                    |
|:----- |:--------------------- |
| `F.L` | `LU`의 `L` (단위 하삼각) 부분 |
| `F.U` | `LU`의 `U` (상삼각) 부분    |
| `F.p` | (오른쪽) 순열 `Vector`     |
| `F.P` | (오른쪽) 순열 `Matrix`     |

분해를 반복하면 구성 요소 `F.L`, `F.U`, 및 `F.p`가 생성됩니다.

# 예제

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # 반복을 통한 구조 분해

julia> l == F.L && u == F.U && p == F.p
true
```
