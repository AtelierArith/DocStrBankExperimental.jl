```
ordschur(F::Schur, select::Union{Vector{Bool},BitVector}) -> F::Schur
```

根据逻辑数组 `select` 重新排序矩阵 `A = Z*T*Z'` 的 Schur 分解 `F`，返回重新排序的分解 `F` 对象。所选的特征值出现在 `F.Schur` 的主对角线上，`F.vectors` 的相应主列形成对应右不变子空间的正交/单位基。在实数情况下，复共轭特征值对必须通过 `select` 要么全部包含，要么全部排除。
