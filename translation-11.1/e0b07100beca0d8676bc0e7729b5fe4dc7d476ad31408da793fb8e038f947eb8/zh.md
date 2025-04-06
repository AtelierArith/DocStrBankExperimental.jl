```
GeneralizedSchur <: Factorization
```

广义 Schur 分解的矩阵分解类型，适用于两个矩阵 `A` 和 `B`。这是 [`schur(_, _)`](@ref) 的返回类型，对应的矩阵分解函数。

如果 `F::GeneralizedSchur` 是分解对象，则可以通过 `F.S` 和 `F.T` 获取（准）三角 Schur 因子，通过 `F.left` 或 `F.Q` 获取左侧单位/正交 Schur 向量，通过 `F.right` 或 `F.Z` 获取右侧单位/正交 Schur 向量，使得 `A=F.left*F.S*F.right'` 和 `B=F.left*F.T*F.right'`。`A` 和 `B` 的广义特征值可以通过 `F.α./F.β` 获取。

迭代分解会产生组件 `F.S`、`F.T`、`F.Q`、`F.Z`、`F.α` 和 `F.β`。
