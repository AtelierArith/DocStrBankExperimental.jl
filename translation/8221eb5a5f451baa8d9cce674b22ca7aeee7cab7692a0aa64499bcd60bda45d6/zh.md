```
potrs!(uplo, A, B)
```

找到 `A * X = B` 的解，其中 `A` 是一个对称或厄米正定矩阵，其 Cholesky 分解是通过 `potrf!` 计算的。如果 `uplo = U`，则计算了 `A` 的上三角 Cholesky 分解。如果 `uplo = L`，则计算了 `A` 的下三角 Cholesky 分解。`B` 被覆盖为解 `X`。
