```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> Eigen
```

计算 `A` 的特征值分解，返回一个 [`Eigen`](@ref) 分解对象 `F`，其中包含特征值在 `F.values` 中，特征向量在矩阵 `F.vectors` 的列中。（第 `k` 个特征向量可以通过切片 `F.vectors[:, k]` 获得。）

迭代分解会产生组件 `F.values` 和 `F.vectors`。

以下函数可用于 `Eigen` 对象：[`inv`](@ref)、[`det`](@ref) 和 [`isposdef`](@ref)。

`vl` 是要搜索的特征值窗口的下界，`vu` 是上界。

!!! note
    如果 [`vl`, `vu`] 不包含 `A` 的所有特征值，则返回的分解将是 *截断* 分解。

