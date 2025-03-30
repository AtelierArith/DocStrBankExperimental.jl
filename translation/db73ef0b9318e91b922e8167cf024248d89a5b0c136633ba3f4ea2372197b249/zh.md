```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> Eigen
```

计算 `A` 的特征值分解，返回一个 [`Eigen`](@ref) 分解对象 `F`，该对象包含特征值在 `F.values` 中，特征向量在矩阵 `F.vectors` 的列中。（第 `k` 个特征向量可以通过切片 `F.vectors[:, k]` 获得。）

迭代分解会产生组件 `F.values` 和 `F.vectors`。

以下函数可用于 `Eigen` 对象：[`inv`](@ref)、[`det`](@ref) 和 [`isposdef`](@ref)。

[`UnitRange`](@ref) `irange` 指定要搜索的排序特征值的索引。

!!! note
    如果 `irange` 不是 `1:n`，其中 `n` 是 `A` 的维度，则返回的分解将是一个 *截断* 分解。

