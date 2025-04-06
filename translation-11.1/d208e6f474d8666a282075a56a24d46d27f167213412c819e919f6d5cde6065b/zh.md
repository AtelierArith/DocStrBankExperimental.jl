```
trsyl!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

解决 Sylvester 矩阵方程 `A * X +/- X * B = scale*C`，其中 `A` 和 `B` 都是准上三角矩阵。如果 `transa = N`，则 `A` 不会被修改。如果 `transa = T`，则 `A` 被转置。如果 `transa = C`，则 `A` 被共轭转置。`transb` 和 `B` 也类似。如果 `isgn = 1`，则方程 `A * X + X * B = scale * C` 被求解。如果 `isgn = -1`，则方程 `A * X - X * B = scale * C` 被求解。

返回 `X`（覆盖 `C`）和 `scale`。
