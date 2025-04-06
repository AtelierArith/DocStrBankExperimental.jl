```
CholeskyPivoted
```

矩阵分解类型，适用于稠密对称/厄米正半定矩阵 `A` 的带主元的 Cholesky 分解。这是 [`cholesky(_, ::RowMaximum)`](@ref) 的返回类型，对应的矩阵分解函数。

可以通过 `F.L` 和 `F.U` 从分解 `F::CholeskyPivoted` 中获得三角形 Cholesky 因子，通过 `F.p` 获得置换，其中 `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'`，其中 `Ur = F.U[1:F.rank, :]` 和 `Lr = F.L[:, 1:F.rank]`，或者替代地 `A ≈ Up' * Up ≈ Lp * Lp'`，其中 `Up = F.U[1:F.rank, invperm(F.p)]` 和 `Lp = F.L[invperm(F.p), 1:F.rank]`。

以下函数可用于 `CholeskyPivoted` 对象：[`size`](@ref)、[`\`](@ref)、[`inv`](@ref)、[`det`](@ref) 和 [`rank`](@ref)。

迭代分解会产生组件 `L` 和 `U`。

# 示例

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U 因子，秩为 1：
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
置换：
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # 通过迭代解构

julia> l == C.L && u == C.U
true
```
