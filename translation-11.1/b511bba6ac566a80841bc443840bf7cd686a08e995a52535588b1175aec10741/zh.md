```
her2k!(uplo, trans, alpha, A, B, beta, C)
```

Hermitian 矩阵 `C` 的 Rank-2k 更新为 `alpha*A*B' + alpha*B*A' + beta*C` 或 `alpha*A'*B + alpha*B'*A + beta*C`，具体取决于 [`trans`](@ref stdlib-blas-trans)。标量 `beta` 必须是实数。仅使用 `C` 的 [`uplo`](@ref stdlib-blas-uplo) 三角部分。返回 `C`。
