```
trrfs!(uplo, trans, diag, A, B, X, Ferr, Berr) -> (Ferr, Berr)
```

估计 `A * X = B` (`trans = N`)、`transpose(A) * X = B` (`trans = T`)、`adjoint(A) * X = B` (`trans = C`) 对于 `side = L` 的解的误差，或者在计算 `X` 后的右侧 `side = R` 的等效方程 `X * A`，使用 `trtrs!`。如果 `uplo = U`，则 `A` 是上三角矩阵。如果 `uplo = L`，则 `A` 是下三角矩阵。如果 `diag = N`，则 `A` 具有非单位对角元素。如果 `diag = U`，则 `A` 的所有对角元素均为一。`Ferr` 和 `Berr` 是可选输入。`Ferr` 是前向误差，`Berr` 是后向误差，均为分量式。
