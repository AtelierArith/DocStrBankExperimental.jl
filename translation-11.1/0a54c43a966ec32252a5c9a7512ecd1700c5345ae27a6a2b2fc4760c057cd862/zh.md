```
syevd!(jobz, uplo, A)
```

查找对称矩阵 `A` 的特征值（`jobz = N`）或特征值和特征向量（`jobz = V`）。如果 `uplo = U`，则使用 `A` 的上三角部分。如果 `uplo = L`，则使用 `A` 的下三角部分。

使用分治法，而不是 `syev!` 使用的 QR 迭代或 `syevr!` 使用的多种相对稳健的表示法。有关不同方法的准确性和性能比较，请参见 James W. Demmel 等人，SIAM J. Sci. Comput. 30, 3, 1508 (2008)。
