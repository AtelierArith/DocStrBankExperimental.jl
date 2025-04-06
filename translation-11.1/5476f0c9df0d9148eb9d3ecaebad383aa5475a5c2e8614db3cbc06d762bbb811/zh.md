```
syevr!(jobz, range, uplo, A, vl, vu, il, iu, abstol) -> (W, Z)
```

查找对称矩阵 `A` 的特征值（`jobz = N`）或特征值和特征向量（`jobz = V`）。如果 `uplo = U`，则使用 `A` 的上三角部分。如果 `uplo = L`，则使用 `A` 的下三角部分。如果 `range = A`，则找到所有特征值。如果 `range = V`，则找到半开区间 `(vl, vu]` 中的特征值。如果 `range = I`，则找到索引在 `il` 和 `iu` 之间的特征值。`abstol` 可以设置为收敛的容差。

特征值返回在 `W` 中，特征向量返回在 `Z` 中。
