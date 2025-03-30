```
trexc!(compq, ifst, ilst, T, Q) -> (T, Q)
trexc!(ifst, ilst, T, Q) -> (T, Q)
```

重新排列矩阵的 Schur 分解 `T`，使得 `T` 中行索引为 `ifst` 的对角块移动到行索引 `ilst`。如果 `compq = V`，则 Schur 向量 `Q` 会被重新排序。如果 `compq = N`，则它们不会被修改。4-参数方法调用 5-参数方法，`compq = V`。
