```
schur(A, B) -> F::GeneralizedSchur
```

计算矩阵 `A` 和 `B` 的广义 Schur（或 QZ）分解。可以通过 `F.S` 和 `F.T` 从 `Schur` 对象 `F` 中获得（准）三角形 Schur 因子，左单位/正交 Schur 向量可以通过 `F.left` 或 `F.Q` 获得，右单位/正交 Schur 向量可以通过 `F.right` 或 `F.Z` 获得，使得 `A=F.left*F.S*F.right'` 和 `B=F.left*F.T*F.right'`。广义特征值 `A` 和 `B` 可以通过 `F.α./F.β` 获得。

迭代分解会产生组件 `F.S`、`F.T`、`F.Q`、`F.Z`、`F.α` 和 `F.β`。
