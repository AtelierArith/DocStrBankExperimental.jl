```
ormrz!(side, trans, A, tau, C)
```

将矩阵 `C` 乘以由 `tzrzf!` 提供的变换中的 `Q`。根据 `side` 或 `trans`，乘法可以是左侧的（`side = L, Q*C`）或右侧的（`side = R, C*Q`），并且 `Q` 可以是未修改的（`trans = N`）、转置的（`trans = T`）或共轭转置的（`trans = C`）。返回矩阵 `C`，该矩阵在原地被修改为乘法的结果。
