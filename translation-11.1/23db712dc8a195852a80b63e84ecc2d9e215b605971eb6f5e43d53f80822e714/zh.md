```
syr2k!(uplo, trans, alpha, A, B, beta, C)
```

对称矩阵 `C` 的秩-2k 更新为 `alpha*A*transpose(B) + alpha*B*transpose(A) + beta*C` 或 `alpha*transpose(A)*B + alpha*transpose(B)*A + beta*C`，具体取决于 [`trans`](@ref stdlib-blas-trans)。仅使用 `C` 的 [`uplo`](@ref stdlib-blas-uplo) 三角部分。返回 `C`。
