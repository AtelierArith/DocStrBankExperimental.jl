```
posv!(uplo, A, B) -> (A, B)
```

找到 `A * X = B` 的解，其中 `A` 是一个对称或厄米正定矩阵。如果 `uplo = U`，则计算 `A` 的上三角 Cholesky 分解。如果 `uplo = L`，则计算 `A` 的下三角 Cholesky 分解。`A` 被其 Cholesky 分解覆盖。`B` 被解 `X` 覆盖。
