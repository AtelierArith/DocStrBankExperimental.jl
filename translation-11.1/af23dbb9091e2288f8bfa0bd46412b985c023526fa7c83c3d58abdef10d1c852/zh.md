```
ormqr!(side, trans, A, tau, C)
```

计算 `Q * C` (`trans = N`)、`transpose(Q) * C` (`trans = T`)、`adjoint(Q) * C` (`trans = C`)，对于 `side = L` 或者使用 `side = R` 的等效右侧乘法，使用从 `geqrf!` 计算的 `A` 的 `QR` 分解中的 `Q`。`C` 被覆盖。
