```
trmv(ul, tA, dA, A, b)
```

返回 `op(A)*b`，其中 `op` 由 [`tA`](@ref stdlib-blas-trans) 确定。仅使用 [`A`](@ref stdlib-blas-uplo) 的 [`ul`](@ref stdlib-blas-uplo) 三角部分。[`dA`](@ref stdlib-blas-diag) 确定是否读取对角线值或假定它们都是一。
