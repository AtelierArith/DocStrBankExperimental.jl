```
getrs!(trans, A, ipiv, B)
```

求解线性方程 `A * X = B`、`transpose(A) * X = B` 或 `adjoint(A) * X = B`，其中 `A` 为方阵。就地修改矩阵/向量 `B` 以得到解。`A` 是来自 `getrf!` 的 `LU` 分解，`ipiv` 是主元信息。`trans` 可以是 `N`（不修改）、`T`（转置）或 `C`（共轭转置）。
