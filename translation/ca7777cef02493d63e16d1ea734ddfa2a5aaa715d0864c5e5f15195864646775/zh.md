```
trsv!(ul, tA, dA, A, b)
```

用 `A*x = b` 的解覆盖 `b`，或根据 [`tA`](@ref stdlib-blas-trans) 和 [`ul`](@ref stdlib-blas-uplo) 确定的其他两个变体之一。 [`dA`](@ref stdlib-blas-diag) 确定是否读取对角线值或假定它们都是一。 返回更新后的 `b`。
