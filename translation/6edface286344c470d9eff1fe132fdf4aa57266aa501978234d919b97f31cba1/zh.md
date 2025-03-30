```
hemm!(side, ul, alpha, A, B, beta, C)
```

根据 [`side`](@ref stdlib-blas-side) 更新 `C` 为 `alpha*A*B + beta*C` 或 `alpha*B*A + beta*C`。假设 `A` 是厄米的。仅使用 `A` 的 [`ul`](@ref stdlib-blas-uplo) 三角部分。返回更新后的 `C`。
