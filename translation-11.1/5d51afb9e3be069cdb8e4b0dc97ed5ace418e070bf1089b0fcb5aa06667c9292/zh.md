```
ordschur(F::GeneralizedSchur, select::Union{Vector{Bool},BitVector}) -> F::GeneralizedSchur
```

根据逻辑数组 `select` 重新排序矩阵对 `(A, B) = (Q*S*Z', Q*T*Z')` 的广义 Schur 分解 `F`，并返回一个广义 Schur 对象 `F`。所选的特征值出现在 `F.S` 和 `F.T` 的主对角线上，左侧和右侧的正交/单位 Schur 向量也被重新排序，以便仍然满足 `(A, B) = F.Q*(F.S, F.T)*F.Z'`，并且仍然可以通过 `F.α./F.β` 获取 `A` 和 `B` 的广义特征值。
