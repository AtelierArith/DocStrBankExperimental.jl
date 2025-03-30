```
cholesky(A, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

밀집 대칭 양의 준정칙 행렬 `A`의 피벗된 Cholesky 분해를 계산하고 [`CholeskyPivoted`](@ref) 분해를 반환합니다. 행렬 `A`는 [`Symmetric`](@ref) 또는 [`Hermitian`](@ref) [`AbstractMatrix`](@ref)일 수 있으며, *완벽하게* 대칭 또는 허미티안 `AbstractMatrix`일 수 있습니다.

삼각형 Cholesky 인자는 분해 `F`에서 `F.L` 및 `F.U`를 통해 얻을 수 있으며, 순열은 `F.p`를 통해 얻을 수 있습니다. 여기서 `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'`이며, `Ur = F.U[1:F.rank, :]` 및 `Lr = F.L[:, 1:F.rank]`입니다. 또는 대안으로 `A ≈ Up' * Up ≈ Lp * Lp'`이며, `Up = F.U[1:F.rank, invperm(F.p)]` 및 `Lp = F.L[invperm(F.p), 1:F.rank]`입니다.

다음 함수는 `CholeskyPivoted` 객체에 대해 사용할 수 있습니다: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), 및 [`rank`](@ref).

인자 `tol`은 랭크를 결정하기 위한 허용 오차를 결정합니다. 음수 값의 경우, 허용 오차는 기계 정밀도입니다.

구성 과정에서 반올림 오류로 인해 약간 비허미티안인 행렬 `A`가 있는 경우, `cholesky`에 전달하기 전에 `Hermitian(A)`로 감싸서 완벽한 허미티안으로 처리하십시오.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임( [`issuccess`](@ref) 사용)은 사용자에게 있습니다.

# 예제

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U 인자는 랭크 1:
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
순열:
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # 반복을 통한 구조 분해

julia> l == C.L && u == C.U
true
```
