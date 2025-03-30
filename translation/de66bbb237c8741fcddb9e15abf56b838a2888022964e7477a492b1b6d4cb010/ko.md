```
bunchkaufman(A, rook::Bool=false; check = true) -> S::BunchKaufman
```

대칭 또는 에르미트 행렬 `A`의 Bunch-Kaufman [^Bunch1977] 분해를 `P'*U*D*U'*P` 또는 `P'*L*D*L'*P` 형태로 계산하고, `A`에 저장된 삼각형에 따라 [`BunchKaufman`](@ref) 객체를 반환합니다. `A`가 복소수 대칭인 경우 `U'`와 `L'`는 비공액 전치(transpose)를 나타내며, 즉 `transpose(U)`와 `transpose(L)`입니다.

분해를 반복하면 `S.uplo`에 따라 적절한 구성 요소인 `S.D`, `S.U` 또는 `S.L`과 `S.p`를 생성합니다.

`rook`이 `true`이면, rook 피벗팅이 사용됩니다. `rook`이 false이면, rook 피벗팅이 사용되지 않습니다.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임은 사용자에게 있습니다 (via [`issuccess`](@ref)).

`BunchKaufman` 객체에 대해 사용할 수 있는 함수는 다음과 같습니다: [`size`](@ref), `\`, [`inv`](@ref), [`issymmetric`](@ref), [`ishermitian`](@ref), [`getindex`](@ref).

[^Bunch1977]: J R Bunch와 L Kaufman, Some stable methods for calculating inertia and solving symmetric linear systems, Mathematics of Computation 31:137 (1977), 163-179. [url](https://www.ams.org/journals/mcom/1977-31-137/S0025-5718-1977-0428694-0/).

# 예제

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A는 내부적으로 Symmetric(A)에 의해 래핑됩니다.
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

julia> S.U*S.D*S.U' - S.P*A*S.P'
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

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

julia> S.L*S.D*S.L' - A[S.p, S.p]
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
