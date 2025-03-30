```
sygvd!(itype, jobz, uplo, A, B) -> (w, A, B)
```

查找对称矩阵 `A` 和对称正定矩阵 `B` 的广义特征值（`jobz = N`）或特征值和特征向量（`jobz = V`）。如果 `uplo = U`，则使用 `A` 和 `B` 的上三角部分。如果 `uplo = L`，则使用 `A` 和 `B` 的下三角部分。如果 `itype = 1`，要解决的问题是 `A * x = lambda * B * x`。如果 `itype = 2`，要解决的问题是 `A * B * x = lambda * x`。如果 `itype = 3`，要解决的问题是 `B * A * x = lambda * x`。
