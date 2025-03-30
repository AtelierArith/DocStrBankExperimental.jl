```
trmm(side, ul, tA, dA, alpha, A, B)
```

返回 `alpha*A*B` 或由 [`side`](@ref stdlib-blas-side) 和 [`tA`](@ref stdlib-blas-trans) 确定的其他三种变体之一。仅使用 `A` 的 [`ul`](@ref stdlib-blas-uplo) 三角形。[`dA`](@ref stdlib-blas-diag) 决定是否读取对角线值或假定它们都是一。
