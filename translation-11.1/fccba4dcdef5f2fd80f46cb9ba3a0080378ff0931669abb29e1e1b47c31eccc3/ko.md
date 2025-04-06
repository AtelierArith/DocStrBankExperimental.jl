```
CholeskyPivoted
```

밀집 대칭/허미티안 양의 준정칙 행렬 `A`의 피벗된 콜레스키 분해의 행렬 분해 유형입니다. 이는 [`cholesky(_, ::RowMaximum)`](@ref)에서 반환되는 유형으로, 해당 행렬 분해 함수입니다.

삼각형 콜레스키 인자는 `F::CholeskyPivoted` 분해에서 `F.L` 및 `F.U`를 통해 얻을 수 있으며, 순열은 `F.p`를 통해 얻을 수 있습니다. 여기서 `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'`이며, `Ur = F.U[1:F.rank, :]` 및 `Lr = F.L[:, 1:F.rank]`로 정의됩니다. 또는 대안으로 `A ≈ Up' * Up ≈ Lp * Lp'`이며, 여기서 `Up = F.U[1:F.rank, invperm(F.p)]` 및 `Lp = F.L[invperm(F.p), 1:F.rank]`로 정의됩니다.

다음 함수들이 `CholeskyPivoted` 객체에 대해 사용 가능합니다: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), 및 [`rank`](@ref).

분해를 반복하면 구성 요소 `L`과 `U`가 생성됩니다.

# 예제

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U factor with rank 1:
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
permutation:
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # destructuring via iteration

julia> l == C.L && u == C.U
true
```
