```
syev!(jobz, uplo, A)
```

查找对称矩阵 `A` 的特征值（`jobz = N`）或特征值和特征向量（`jobz = V`）。如果 `uplo = U`，则使用 `A` 的上三角部分。如果 `uplo = L`，则使用 `A` 的下三角部分。
