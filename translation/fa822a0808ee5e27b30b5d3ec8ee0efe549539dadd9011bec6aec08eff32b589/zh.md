```
herk!(uplo, trans, alpha, A, beta, C)
```

仅适用于复数数组。根据 [`trans`](@ref stdlib-blas-trans)，对厄米矩阵 `C` 进行秩-k 更新，形式为 `alpha*A*A' + beta*C` 或 `alpha*A'*A + beta*C`。仅更新 `C` 的 [`uplo`](@ref stdlib-blas-uplo) 三角部分。返回 `C`。
