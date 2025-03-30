```
trsv(ul, tA, dA, A, b)
```

返回 `A*x = b` 的解，或由 [`tA`](@ref stdlib-blas-trans) 和 [`ul`](@ref stdlib-blas-uplo) 确定的其他两个变体。[`dA`](@ref stdlib-blas-diag) 确定对角线值是被读取还是假定为全为一。
