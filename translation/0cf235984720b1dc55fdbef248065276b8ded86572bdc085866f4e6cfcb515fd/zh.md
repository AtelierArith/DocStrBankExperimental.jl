```
ldlt(A::SparseMatrixCSC; shift = 0.0, check = true, perm=nothing) -> CHOLMOD.Factor
```

计算稀疏矩阵 `A` 的 $LDL'$ 分解。`A` 必须是 [`SparseMatrixCSC`](@ref) 或 `SparseMatrixCSC` 的 [`Symmetric`](@ref)/[`Hermitian`](@ref) 视图。请注意，即使 `A` 没有类型标签，它仍然必须是对称或厄米的。使用填充减少的置换。`F = ldlt(A)` 最常用于求解方程组 `A*x = b`，使用 `F\b`。返回的分解对象 `F` 还支持方法 [`diag`](@ref)、[`det`](@ref)、[`logdet`](@ref) 和 [`inv`](@ref)。您可以使用 `F.L` 从 `F` 中提取单个因子。然而，由于默认情况下启用了主元，分解在内部表示为 `A == P'*L*D*L'*P`，其中 `P` 是置换矩阵；仅使用 `L` 而不考虑 `P` 将给出不正确的答案。为了包括置换的影响，通常更好地提取“组合”因子，如 `PtL = F.PtL`（相当于 `P'*L`）和 `LtP = F.UP`（相当于 `L'*P`）。支持的因子完整列表为 `:L, :PtL, :D, :UP, :U, :LD, :DU, :PtLD, :DUP`。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）由用户承担。

设置可选的 `shift` 关键字参数计算 `A+shift*I` 的分解，而不是 `A`。如果提供了 `perm` 参数，它应该是 `1:size(A,1)` 的一个置换，给出要使用的顺序（而不是 CHOLMOD 的默认 AMD 顺序）。

!!! note
    此方法使用来自 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse) 的 CHOLMOD[^ACM887][^DavisHager2009] 库。CHOLMOD 仅支持单精度或双精度的实数或复数类型。输入矩阵如果不是这些元素类型，将根据需要转换为这些类型。

    CHOLMOD 的许多其他函数被封装但未从 `Base.SparseArrays.CHOLMOD` 模块导出。

