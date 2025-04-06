```
BunchKaufman <: Factorization
```

대칭 또는 에르미트 행렬 `A`의 Bunch-Kaufman 분해의 행렬 분해 유형으로, `A`에 상단(기본값) 또는 하단 삼각형이 저장되는지에 따라 `P'UDU'P` 또는 `P'LDL'P`로 표현됩니다. `A`가 복소수 대칭인 경우 `U'`와 `L'`는 비공액 전치(transpose)를 나타내며, 즉 각각 `transpose(U)`와 `transpose(L)`입니다. 이는 [`bunchkaufman`](@ref) 함수의 반환 유형입니다.

`S::BunchKaufman`이 분해 객체인 경우, 구성 요소는 `S.uplo` 및 `S.p`에 따라 적절하게 `S.D`, `S.U` 또는 `S.L`을 통해 얻을 수 있습니다.

분해를 반복하면 `S.uplo` 및 `S.p`에 따라 적절하게 `S.D`, `S.U` 또는 `S.L` 구성 요소가 생성됩니다.

# 예제

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A는 내부적으로 Symmetric(A)로 래핑됩니다.
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D 인자:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
U 인자:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
순열:
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # 반복을 통한 구조 분해

julia> d == S.D && u == S.U && p == S.p
true

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D 인자:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
L 인자:
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
순열:
2-element Vector{Int64}:
 2
 1
```
