```
syrk!(uplo, trans, alpha, A, beta, C)
```

对称矩阵 `C` 的秩-k 更新为 `alpha*A*transpose(A) + beta*C` 或 `alpha*transpose(A)*A + beta*C`，具体取决于 [`trans`](@ref stdlib-blas-trans)。仅使用 `C` 的 [`uplo`](@ref stdlib-blas-uplo) 三角部分。返回 `C`。
