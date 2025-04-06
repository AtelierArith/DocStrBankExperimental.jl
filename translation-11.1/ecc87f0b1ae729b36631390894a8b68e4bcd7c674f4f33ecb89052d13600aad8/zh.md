```
SparseArrays.sparse!(I, J, V, [m, n, combine]) -> SparseMatrixCSC
```

`sparse!` 的变体，重新使用输入向量（`I`，`J`，`V`）作为最终矩阵存储。在构造后，输入向量将别名矩阵缓冲区；`S.colptr === I`，`S.rowval === J`，和 `S.nzval === V` 成立，并且它们会根据需要进行 `resize!`。

请注意，仍然会分配一些工作缓冲区。具体来说，此方法是 `sparse!(I, J, V, m, n, combine, klasttouch, csrrowptr, csrcolval, csrnzval, csccolptr, cscrowval, cscnzval)` 的便利包装，其中此方法分配适当大小的 `klasttouch`，`csrrowptr`，`csrcolval` 和 `csrnzval`，但重用 `I`，`J` 和 `V` 作为 `csccolptr`，`cscrowval` 和 `cscnzval`。

参数 `m`，`n` 和 `combine` 默认为 `maximum(I)`，`maximum(J)` 和 `+`，分别。

!!! compat "Julia 1.10"
    此方法需要 Julia 1.10 或更高版本。

