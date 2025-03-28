```
ormql!(side, trans, A, tau, C)
```

`Q * C` を計算します（`trans = N`）、`transpose(Q) * C`（`trans = T`）、`adjoint(Q) * C`（`trans = C`）は `side = L` の場合、または `side = R` の場合は `A` の `QL` 因子分解から計算された `Q` を使用して同等の右側の乗算を行います。`C` は上書きされます。
