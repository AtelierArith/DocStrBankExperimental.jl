```
permute!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti},
         p::AbstractVector{<:Integer}, q::AbstractVector{<:Integer},
         [C::AbstractSparseMatrixCSC{Tv,Ti}]) where {Tv,Ti}
```

双向置换 `A`，将结果 `PAQ` (`A[p,q]`) 存储在 `X` 中。如果存在，则将中间结果 `(AQ)^T` (`transpose(A[:,q])`) 存储在可选参数 `C` 中。要求 `X`、`A`，以及（如果存在）`C` 之间没有别名；要将结果 `PAQ` 存回 `A`，请使用以下不带 `X` 的方法：

```
permute!(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
         q::AbstractVector{<:Integer}[, C::AbstractSparseMatrixCSC{Tv,Ti},
         [workcolptr::Vector{Ti}]]) where {Tv,Ti}
```

`X` 的维度必须与 `A` 匹配（`size(X, 1) == size(A, 1)` 和 `size(X, 2) == size(A, 2)`），并且 `X` 必须有足够的存储空间来容纳 `A` 中的所有分配条目（`length(rowvals(X)) >= nnz(A)` 和 `length(nonzeros(X)) >= nnz(A)`）。列置换 `q` 的长度必须与 `A` 的列数匹配（`length(q) == size(A, 2)`）。行置换 `p` 的长度必须与 `A` 的行数匹配（`length(p) == size(A, 1)`）。

`C` 的维度必须与 `transpose(A)` 匹配（`size(C, 1) == size(A, 2)` 和 `size(C, 2) == size(A, 1)`），并且 `C` 必须有足够的存储空间来容纳 `A` 中的所有分配条目（`length(rowvals(C)) >= nnz(A)` 和 `length(nonzeros(C)) >= nnz(A)`）。

有关更多（算法）信息，以及放弃参数检查的这些方法的版本，请参见（未导出的）父方法 `unchecked_noalias_permute!` 和 `unchecked_aliasing_permute!`。

另见 [`permute`](@ref).
