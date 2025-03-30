```
adjoint!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

转置矩阵 `A` 并将元素的伴随存储在矩阵 `X` 中。`size(X)` 必须等于 `size(transpose(A))`。除了在需要时调整 `X` 的 `rowval` 和 `nzval` 之外，不会分配额外的内存。

请参见 `halfperm!`
