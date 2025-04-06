```
SparseArrays.spzeros!(::Type{Tv}, I, J, [m, n]) -> SparseMatrixCSC{Tv}
```

`spzeros!` 的变体，重新使用输入向量 `I` 和 `J` 作为最终矩阵存储。在构造后，输入向量将别名矩阵缓冲区；`S.colptr === I` 和 `S.rowval === J` 成立，并且它们会根据需要进行 `resize!`。

请注意，仍然会分配一些工作缓冲区。具体来说，此方法是 `spzeros!(Tv, I, J, m, n, klasttouch, csrrowptr, csrcolval, csccolptr, cscrowval)` 的便利包装，其中此方法分配适当大小的 `klasttouch`、`csrrowptr` 和 `csrcolval`，但重新使用 `I` 和 `J` 作为 `csccolptr` 和 `cscrowval`。

参数 `m` 和 `n` 默认为 `maximum(I)` 和 `maximum(J)`。

!!! compat "Julia 1.10"
    此方法需要 Julia 1.10 或更高版本。

