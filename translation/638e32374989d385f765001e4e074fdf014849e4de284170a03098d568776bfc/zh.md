```
gemmt!(uplo, tA, tB, alpha, A, B, beta, C)
```

根据 [`uplo`](@ref stdlib-blas-uplo) 指定的下三角或上三角部分更新 `C`，计算为 `alpha*A*B + beta*C` 或根据 [`tA`](@ref stdlib-blas-trans) 和 `tB` 的其他变体。返回更新后的 `C`。

!!! compat "Julia 1.11"
    `gemmt!` 至少需要 Julia 1.11。

