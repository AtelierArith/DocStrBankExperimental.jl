```
trsen!(job, compq, select, T, Q) -> (T, Q, w, s, sep)
trsen!(select, T, Q) -> (T, Q, w, s, sep)
```

重新排序矩阵的 Schur 分解，并可选择性地找到倒数条件数。如果 `job = N`，则不找到条件数。如果 `job = E`，则仅找到此特征值簇的条件数。如果 `job = V`，则仅找到不变子空间的条件数。如果 `job = B`，则找到簇和子空间的条件数。如果 `compq = V`，则更新 Schur 向量 `Q`。如果 `compq = N`，则不修改 Schur 向量。`select` 确定哪些特征值在簇中。3 参数方法调用 5 参数方法，`job = N` 和 `compq = V`。

返回 `T`，`Q`，重新排序的特征值 `w`，特征值簇的条件数 `s`，以及不变子空间的条件数 `sep`。
