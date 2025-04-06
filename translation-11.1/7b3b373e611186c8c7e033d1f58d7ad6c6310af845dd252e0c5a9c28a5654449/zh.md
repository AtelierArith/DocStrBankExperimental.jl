```
halfperm!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{TvA,Ti},
          q::AbstractVector{<:Integer}, f::Function = identity) where {Tv,TvA,Ti}
```

列置换并转置 `A`，同时对 `A` 的每个条目应用 `f`，将结果 `(f(A)Q)^T` (`map(f, transpose(A[:,q]))`) 存储在 `X` 中。

`X` 的元素类型 `Tv` 必须与 `f(::TvA)` 匹配，其中 `TvA` 是 `A` 的元素类型。`X` 的维度必须与 `transpose(A)` 匹配（`size(X, 1) == size(A, 2)` 和 `size(X, 2) == size(A, 1)`），并且 `X` 必须有足够的存储空间来容纳 `A` 中的所有分配条目（`length(rowvals(X)) >= nnz(A)` 和 `length(nonzeros(X)) >= nnz(A)`）。列置换 `q` 的长度必须与 `A` 的列数匹配（`length(q) == size(A, 2)`）。

此方法是执行 [`SparseMatrixCSC`](@ref) 上的转置和置换操作的多个方法的父方法。由于此方法不执行参数检查，因此更倾向于使用更安全的子方法（`[c]transpose[!]`，`permute[!]`）而不是直接使用。

此方法实现了 F. Gustavson 描述的 `HALFPERM` 算法，"Two fast algorithms for sparse matrices: multiplication and permuted transposition," ACM TOMS 4(3), 250-269 (1978)。该算法的运行时间为 `O(size(A, 1), size(A, 2), nnz(A))`，并且不需要超出传入的空间。
