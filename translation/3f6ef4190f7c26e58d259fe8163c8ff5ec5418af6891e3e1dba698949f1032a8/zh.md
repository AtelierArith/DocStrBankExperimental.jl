```
gemm!(tA, tB, alpha, A, B, beta, C)
```

更新 `C` 为 `alpha*A*B + beta*C` 或根据 [`tA`](@ref stdlib-blas-trans) 和 `tB` 的其他三种变体。返回更新后的 `C`。
