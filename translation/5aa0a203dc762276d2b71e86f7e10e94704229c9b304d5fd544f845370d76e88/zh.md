```
trsm!(side, ul, tA, dA, alpha, A, B)
```

用 `A*X = alpha*B` 的解覆盖 `B`，或根据 [`side`](@ref stdlib-blas-side) 和 [`tA`](@ref stdlib-blas-trans) 确定的其他三种变体之一。仅使用 `A` 的 [`ul`](@ref stdlib-blas-uplo) 三角形。[`dA`](@ref stdlib-blas-diag) 决定是否读取对角线值或假定它们都是一。返回更新后的 `B`。
