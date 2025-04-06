```
spzeros([type], I::AbstractVector, J::AbstractVector, [m, n])
```

创建一个维度为 `m x n` 的稀疏矩阵 `S`，在 `S[I[k], J[k]]` 处具有结构零。

此方法可用于构造矩阵的稀疏模式，并且比使用例如 `sparse(I, J, zeros(length(I)))` 更高效。

有关更多文档和专家驱动程序，请参见 `SparseArrays.spzeros!`。

!!! compat "Julia 1.10"
    此方法需要 Julia 版本 1.10 或更高版本。

