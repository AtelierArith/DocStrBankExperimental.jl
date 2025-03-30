```
symm(side, ul, alpha, A, B)
```

返回 `alpha*A*B` 或 `alpha*B*A`，具体取决于 [`side`](@ref stdlib-blas-side)。假设 `A` 是对称的。仅使用 `A` 的 [`ul`](@ref stdlib-blas-uplo) 三角部分。
