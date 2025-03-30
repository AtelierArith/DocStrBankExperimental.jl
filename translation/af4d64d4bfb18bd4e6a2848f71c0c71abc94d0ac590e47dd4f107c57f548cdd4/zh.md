```
LinearAlgebra.Givens(i1,i2,c,s) -> G
```

一个 Givens 旋转线性算子。字段 `c` 和 `s` 分别表示旋转角度的余弦和正弦。`Givens` 类型支持左乘 `G*A` 和共轭转置右乘 `A*G'`。该类型没有 `size`，因此可以与任意大小的矩阵相乘，只要 `i2<=size(A,2)` 对于 `G*A` 或 `i2<=size(A,1)` 对于 `A*G'`。

另见 [`givens`](@ref)。
