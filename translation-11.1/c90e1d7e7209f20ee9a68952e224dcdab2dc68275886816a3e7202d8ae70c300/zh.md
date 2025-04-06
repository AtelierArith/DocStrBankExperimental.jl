```
cholesky(A, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

计算稠密对称半正定矩阵 `A` 的带主元的 Cholesky 分解，并返回一个 [`CholeskyPivoted`](@ref) 分解。矩阵 `A` 可以是 [`Symmetric`](@ref) 或 [`Hermitian`](@ref) [`AbstractMatrix`](@ref)，或者是 *完全* 对称或 Hermitian 的 `AbstractMatrix`。

可以通过 `F.L` 和 `F.U` 从分解 `F` 中获得三角 Cholesky 因子，以及通过 `F.p` 获得置换，其中 `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'`，其中 `Ur = F.U[1:F.rank, :]` 和 `Lr = F.L[:, 1:F.rank]`，或者替代地 `A ≈ Up' * Up ≈ Lp * Lp'`，其中 `Up = F.U[1:F.rank, invperm(F.p)]` 和 `Lp = F.L[invperm(F.p), 1:F.rank]`。

以下函数可用于 `CholeskyPivoted` 对象：[`size`](@ref)、[`\`](@ref)、[`inv`](@ref)、[`det`](@ref) 和 [`rank`](@ref)。

参数 `tol` 决定了确定秩的容差。对于负值，容差为机器精度。

如果您有一个由于构造中的舍入误差而略微非 Hermitian 的矩阵 `A`，请在将其传递给 `cholesky` 之前用 `Hermitian(A)` 将其包装，以便将其视为完全 Hermitian。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）在于用户。

# 示例

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
