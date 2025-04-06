```
ftranspose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}, f::Function) where {Tv,Ti}
```

转置 `A` 并将其存储在 `X` 中，同时对非零元素应用函数 `f`。不会移除 `f` 创建的零。`size(X)` 必须等于 `size(transpose(A))`。除了在需要时调整 `X` 的 `rowval` 和 `nzval` 之外，不会分配额外的内存。

请参见 `halfperm!`
