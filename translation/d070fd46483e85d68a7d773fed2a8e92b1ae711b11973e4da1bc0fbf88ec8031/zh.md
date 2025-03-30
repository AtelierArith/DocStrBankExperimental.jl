```
hemv!(ul, alpha, A, x, beta, y)
```

更新向量 `y` 为 `alpha*A*x + beta*y`。假设 `A` 是厄米的。仅使用 `A` 的 [`ul`](@ref stdlib-blas-uplo) 三角部分。`alpha` 和 `beta` 是标量。返回更新后的 `y`。
