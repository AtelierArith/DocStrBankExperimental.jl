```
sytrf!(uplo, A) -> (A, ipiv, info)
```

计算对称矩阵 `A` 的 Bunch-Kaufman 分解。如果 `uplo = U`，则存储 `A` 的上半部分。如果 `uplo = L`，则存储下半部分。

返回被分解覆盖的 `A`、一个主元向量 `ipiv` 和错误代码 `info`，该代码是一个非负整数。如果 `info` 为正，则矩阵是奇异的，分解的对角部分在位置 `info` 处恰好为零。
