```
gttrs!(trans, dl, d, du, du2, ipiv, B)
```

求解方程 `A * X = B` (`trans = N`)、`transpose(A) * X = B` (`trans = T`) 或 `adjoint(A) * X = B` (`trans = C`)，使用通过 `gttrf!` 计算的 `LU` 分解。`B` 被覆盖为解 `X`。
