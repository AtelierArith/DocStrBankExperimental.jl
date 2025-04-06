```
ormql!(side, trans, A, tau, C)
```

计算 `Q * C` (`trans = N`)、`transpose(Q) * C` (`trans = T`)、`adjoint(Q) * C` (`trans = C`)，对于 `side = L` 或者使用从 `geqlf!` 计算的 `A` 的 `QL` 分解得到的 `Q` 进行等效的右侧乘法 `side = R`。`C` 被覆盖。
