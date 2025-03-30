```
potrf!(uplo, A)
```

计算正定矩阵 `A` 的 Cholesky 分解（如果 `uplo = U` 则为上三角，如果 `uplo = L` 则为下三角）。`A` 被覆盖并返回一个信息代码。
