```
gemqrt!(side, trans, V, T, C)
```

`Q * C` を計算します（`trans = N`）、`transpose(Q) * C`（`trans = T`）、`adjoint(Q) * C`（`trans = C`）で `side = L` または `side = R` の場合は `geqrt!` を使用して計算された `A` の `QR` 分解からの `Q` を使用します。`C` は上書きされます。
