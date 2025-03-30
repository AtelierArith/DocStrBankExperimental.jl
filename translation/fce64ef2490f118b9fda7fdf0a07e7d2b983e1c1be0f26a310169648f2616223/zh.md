```
ormrq!(side, trans, A, tau, C)
```

计算 `Q * C`（`trans = N`）、`transpose(Q) * C`（`trans = T`）、`adjoint(Q) * C`（`trans = C`）对于 `side = L` 或者使用从 `gerqf!` 计算的 `A` 的 `RQ` 分解得到的 `Q` 进行等效的右侧乘法对于 `side = R`。`C` 被覆盖。
