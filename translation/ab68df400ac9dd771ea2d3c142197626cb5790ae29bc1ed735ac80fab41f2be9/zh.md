```
hetri!(uplo, A, ipiv)
```

计算 Hermitian 矩阵 `A` 的逆，使用 `sytrf!` 的结果。如果 `uplo = U`，则存储 `A` 的上半部分。如果 `uplo = L`，则存储下半部分。`A` 被其逆覆盖。
