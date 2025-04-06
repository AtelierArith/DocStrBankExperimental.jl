```
pstrf!(uplo, A, tol) -> (A, piv, rank, info)
```

计算正定矩阵 `A` 的（如果 `uplo = U` 则为上三角，如果 `uplo = L` 则为下三角）带主元的 Cholesky 分解，使用用户设置的容忍度 `tol`。`A` 被其 Cholesky 分解覆盖。

返回 `A`、主元 `piv`、`A` 的秩，以及一个 `info` 代码。如果 `info = 0`，则分解成功。如果 `info = i > 0`，则 `A` 是不定的或秩不足。
