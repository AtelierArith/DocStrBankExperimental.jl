```
hetrs!(uplo, A, ipiv, B)
```

求解方程 `A * X = B`，其中 `A` 是一个厄米矩阵，使用 `sytrf!` 的结果。如果 `uplo = U`，则存储 `A` 的上半部分。如果 `uplo = L`，则存储下半部分。`B` 被解 `X` 覆盖。
