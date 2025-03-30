```
transpose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

转置矩阵 `A` 并将其存储在矩阵 `X` 中。`size(X)` 必须等于 `size(transpose(A))`。除非需要调整 `X` 的 `rowval` 和 `nzval`，否则不分配额外的内存。

请参见 `halfperm!`
