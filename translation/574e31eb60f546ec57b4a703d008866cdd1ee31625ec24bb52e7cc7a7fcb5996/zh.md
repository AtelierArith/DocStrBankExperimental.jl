```
cholesky(A::SparseMatrixCSC; shift = 0.0, check = true, perm = nothing) -> CHOLMOD.Factor
```

计算稀疏正定矩阵 `A` 的 Cholesky 分解。`A` 必须是 [`SparseMatrixCSC`](@ref) 或 `SparseMatrixCSC` 的 [`Symmetric`](@ref)/[`Hermitian`](@ref) 视图。请注意，即使 `A` 没有类型标签，它仍然必须是对称的或厄米的。如果未给出 `perm`，则使用填充减少的置换。`F = cholesky(A)` 最常用于通过 `F\b` 求解方程组，但方法 [`diag`](@ref)、[`det`](@ref) 和 [`logdet`](@ref) 也为 `F` 定义。您还可以使用 `F.L` 提取单个因子。然而，由于默认情况下启用了主元，因子分解在内部表示为 `A == P'*L*L'*P`，其中 `P` 是置换矩阵；仅使用 `L` 而不考虑 `P` 将给出不正确的答案。为了包括置换的影响，通常更可取的是提取“组合”因子，如 `PtL = F.PtL`（相当于 `P'*L`）和 `LtP = F.UP`（相当于 `L'*P`）。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）由用户承担。

设置可选的 `shift` 关键字参数将计算 `A+shift*I` 的分解，而不是 `A`。如果提供了 `perm` 参数，它应该是 `1:size(A,1)` 的一个置换，给出要使用的顺序（而不是 CHOLMOD 的默认 AMD 顺序）。

# 示例

在以下示例中，使用的填充减少置换是 `[3, 2, 1]`。如果将 `perm` 设置为 `1:3` 以强制不进行置换，则因子中的非零元素数量为 6。

```jldoctest
julia> A = [2 1 1; 1 2 0; 1 0 2]
3×3 Matrix{Int64}:
 2  1  1
 1  2  0
 1  0  2

julia> C = cholesky(sparse(A))
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  5
nnz:     5
success: true

julia> C.p
3-element Vector{Int64}:
 3
 2
 1

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421   0.0       0.0
 0.0       1.41421   0.0
 0.707107  0.707107  1.0

julia> L * L' ≈ A[C.p, C.p]
true

julia> P = sparse(1:3, C.p, ones(3))
3×3 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
  ⋅    ⋅   1.0
  ⋅   1.0   ⋅
 1.0   ⋅    ⋅

julia> P' * L * L' * P ≈ A
true

julia> C = cholesky(sparse(A), perm=1:3)
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  6
nnz:     6
success: true

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421    0.0       0.0
 0.707107   1.22474   0.0
 0.707107  -0.408248  1.1547

julia> L * L' ≈ A
true
```

!!! note
    此方法使用来自 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) 的 CHOLMOD[^ACM887][^DavisHager2009] 库。CHOLMOD 仅支持单精度或双精度的实数或复数类型。输入矩阵如果不是这些元素类型，将适当地转换为这些类型。

    CHOLMOD 的许多其他函数被封装但未从 `Base.SparseArrays.CHOLMOD` 模块导出。


[^ACM887]: Chen, Y., Davis, T. A., Hager, W. W., & Rajamanickam, S. (2008). Algorithm 887: CHOLMOD, Supernodal Sparse Cholesky Factorization and Update/Downdate. ACM Trans. Math. Softw., 35(3). [doi:10.1145/1391989.1391995](https://doi.org/10.1145/1391989.1391995)

[^DavisHager2009]: Davis, Timothy A., & Hager, W. W. (2009). Dynamic Supernodes in Sparse Cholesky Update/Downdate and Triangular Solves. ACM Trans. Math. Softw., 35(4). [doi:10.1145/1462173.1462176](https://doi.org/10.1145/1462173.1462176)
