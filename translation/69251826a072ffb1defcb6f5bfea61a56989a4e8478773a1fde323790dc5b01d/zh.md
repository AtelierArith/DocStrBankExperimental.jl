```
gemv!(tA, alpha, A, x, beta, y)
```

更新向量 `y` 为 `alpha*A*x + beta*y` 或 `alpha*A'x + beta*y`，具体取决于 [`tA`](@ref stdlib-blas-trans)。`alpha` 和 `beta` 是标量。返回更新后的 `y`。
