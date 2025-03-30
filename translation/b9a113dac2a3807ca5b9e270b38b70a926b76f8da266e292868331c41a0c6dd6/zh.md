```
syr!(uplo, alpha, x, A)
```

对称矩阵 `A` 的秩-1 更新，使用向量 `x` 进行更新，形式为 `alpha*x*transpose(x) + A`。[`uplo`](@ref stdlib-blas-uplo) 控制更新 `A` 的哪个三角部分。返回 `A`。
