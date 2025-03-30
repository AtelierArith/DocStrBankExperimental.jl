```
factorize(A)
```

입력 행렬의 유형에 따라 `A`의 편리한 인수 분해를 계산합니다. `factorize`는 `A`가 일반 행렬로 전달되면 대칭/삼각형/etc.인지 확인합니다. `factorize`는 `A`의 각 요소를 확인하여 각 속성을 검증/배제합니다. 대칭/삼각형 구조를 배제할 수 있는 즉시 단축 회로를 사용합니다. 반환 값은 여러 시스템을 효율적으로 해결하는 데 재사용할 수 있습니다. 예를 들어: `A=factorize(A); x=A\b; y=A\C`.

| `A`의 속성     | 인수 분해 유형                                   |
|:----------- |:------------------------------------------ |
| 양의 정부호      | Cholesky (see [`cholesky`](@ref))          |
| 밀집 대칭/에르미트  | Bunch-Kaufman (see [`bunchkaufman`](@ref)) |
| 희소 대칭/에르미트  | LDLt (see [`ldlt`](@ref))                  |
| 삼각형         | 삼각형                                        |
| 대각선         | 대각선                                        |
| 이대각선        | 이대각선                                       |
| 삼중대각선       | LU (see [`lu`](@ref))                      |
| 대칭 실수 삼중대각선 | LDLt (see [`ldlt`](@ref))                  |
| 일반 정사각형     | LU (see [`lu`](@ref))                      |
| 일반 비정사각형    | QR (see [`qr`](@ref))                      |

예를 들어 `factorize`가 에르미트 양의 정부호 행렬에 호출되면, `factorize`는 Cholesky 인수 분해를 반환합니다.

# 예제

```jldoctest
julia> A = Array(Bidiagonal(fill(1.0, (5, 5)), :U))
5×5 Matrix{Float64}:
 1.0  1.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  1.0

julia> factorize(A) # factorize는 A가 이미 인수 분해되었는지 확인합니다
5×5 Bidiagonal{Float64, Vector{Float64}}:
 1.0  1.0   ⋅    ⋅    ⋅
  ⋅   1.0  1.0   ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅    ⋅   1.0
```

이것은 이제 다른 선형 대수 함수(예: 고유값 해결기)에 전달될 수 있는 `5×5 Bidiagonal{Float64}`를 반환하며, 이 함수는 `Bidiagonal` 유형에 대한 특수화된 방법을 사용할 것입니다.
