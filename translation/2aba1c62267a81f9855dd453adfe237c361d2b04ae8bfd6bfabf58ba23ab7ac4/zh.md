```
potri!(uplo, A)
```

计算正定矩阵 `A` 的逆，在调用 `potrf!` 找到其（如果 `uplo = U` 则为上三角，如果 `uplo = L` 则为下三角）Cholesky 分解后。

`A` 被其逆覆盖并返回。
