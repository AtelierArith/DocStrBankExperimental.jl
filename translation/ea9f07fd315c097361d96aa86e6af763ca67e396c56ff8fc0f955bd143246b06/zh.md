```
her!(uplo, alpha, x, A)
```

仅适用于复数数组。对厄米矩阵 `A` 进行秩-1 更新，使用向量 `x` 进行更新，形式为 `alpha*x*x' + A`。[`uplo`](@ref stdlib-blas-uplo) 控制更新 `A` 的哪个三角部分。返回 `A`。
