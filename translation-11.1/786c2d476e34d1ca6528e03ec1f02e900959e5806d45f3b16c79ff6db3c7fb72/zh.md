```
ggsvd!(jobu, jobv, jobq, A, B) -> (U, V, Q, alpha, beta, k, l, R)
```

找到 `A` 和 `B` 的广义奇异值分解，`U'*A*Q = D1*R` 和 `V'*B*Q = D2*R`。`D1` 的对角线上有 `alpha`，`D2` 的对角线上有 `beta`。如果 `jobu = U`，则计算正交/单位矩阵 `U`。如果 `jobv = V`，则计算正交/单位矩阵 `V`。如果 `jobq = Q`，则计算正交/单位矩阵 `Q`。如果 `jobu`、`jobv` 或 `jobq` 为 `N`，则不计算该矩阵。此函数仅在 3.6.0 之前的 LAPACK 版本中可用。
