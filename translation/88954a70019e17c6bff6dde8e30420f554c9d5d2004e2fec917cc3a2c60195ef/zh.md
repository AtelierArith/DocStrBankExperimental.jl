```
sysv!(uplo, A, B) -> (B, A, ipiv)
```

找到对称矩阵 `A` 的 `A * X = B` 的解。如果 `uplo = U`，则存储 `A` 的上半部分。如果 `uplo = L`，则存储下半部分。`B` 被解 `X` 覆盖。`A` 被其 Bunch-Kaufman 分解覆盖。`ipiv` 包含关于分解的主元信息。
