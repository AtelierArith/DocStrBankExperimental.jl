```
lu(A, pivot = RowMaximum(); check = true, allowsingular = false) -> F::LU
```

행렬 `A`의 LU 분해를 계산합니다.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임은 사용자에게 있습니다 (via [`issuccess`](@ref)).

기본적으로, `check = true`일 때, 분해가 유효한 요소를 생성하더라도 상삼각 행렬 `U`가 랭크 결핍인 경우에도 오류가 발생합니다. 이는 `allowsingular = true`를 전달하여 변경할 수 있습니다.

대부분의 경우, `A`가 `AbstractMatrix{T}`의 하위 유형 `S`이고 요소 유형 `T`가 `+`, `-`, `*` 및 `/`를 지원하는 경우, 반환 유형은 `LU{T,S{T}}`입니다.

일반적으로 LU 분해는 행렬의 행을 순열하는 것을 포함하며 (아래에 설명된 `F.p` 출력에 해당), 이를 "피벗팅"이라고 합니다 (이는 "피벗"이 포함된 행, 즉 `F.U`의 대각선 항목을 선택하는 것과 관련이 있습니다). 다음의 피벗팅 전략 중 하나를 선택할 수 있습니다:

  * `RowMaximum()` (기본값): 표준 피벗팅 전략; 피벗은 남아 있는, 분해될 행 중 최대 절대값을 가지는 요소에 해당합니다. 이 피벗팅 전략은 요소 유형이 [`abs`](@ref) 및 [`<`](@ref)도 지원해야 합니다. (이는 일반적으로 부동 소수점 행렬에 대해 유일하게 수치적으로 안정적인 옵션입니다.)
  * `RowNonZero()`: 피벗은 남아 있는, 분해될 행 중 첫 번째 비영(非零) 요소에 해당합니다. (이는 수작업 계산에서 일반적인 선택에 해당하며, [`iszero`](@ref)를 지원하지만 `abs` 또는 `<`를 지원하지 않는 보다 일반적인 대수적 수 유형에도 유용합니다.)
  * `NoPivot()`: 피벗팅이 꺼집니다 (피벗 위치에서 0 항목이 발견되면 실패하며, `allowsingular = true`일 때도 마찬가지입니다).

분해 `F`의 개별 구성 요소는 [`getproperty`](@ref)를 통해 접근할 수 있습니다:

| 구성 요소 | 설명                 |
|:----- |:------------------ |
| `F.L` | `LU`의 `L` (하삼각) 부분 |
| `F.U` | `LU`의 `U` (상삼각) 부분 |
| `F.p` | (오른쪽) 순열 `Vector`  |
| `F.P` | (오른쪽) 순열 `Matrix`  |

분해를 반복하면 구성 요소 `F.L`, `F.U`, 및 `F.p`가 생성됩니다.

`F`와 `A`의 관계는 다음과 같습니다.

`F.L*F.U == A[F.p, :]`

`F`는 다음 함수를 추가로 지원합니다:

| 지원 함수               | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------- |:---- |:---------------------- |
| [`/`](@ref)         | ✓    |                        |
| [`\`](@ref)         | ✓    | ✓                      |
| [`inv`](@ref)       | ✓    | ✓                      |
| [`det`](@ref)       | ✓    | ✓                      |
| [`logdet`](@ref)    | ✓    | ✓                      |
| [`logabsdet`](@ref) | ✓    | ✓                      |
| [`size`](@ref)      | ✓    | ✓                      |

!!! compat "Julia 1.11"
    `allowsingular` 키워드 인자는 Julia 1.11에서 추가되었습니다.


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

julia> lu([1 2; 1 2], allowsingular = true)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0  0.0
 1.0  1.0
U factor (rank-deficient):
2×2 Matrix{Float64}:
 1.0  2.0
 0.0  0.0
```
