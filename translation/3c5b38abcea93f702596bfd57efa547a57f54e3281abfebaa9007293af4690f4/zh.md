```
RowSlices{M,AX,S}
```

[`RowSlices`](@ref) 是 [`Slices`](@ref) 的一个特例，它是一个矩阵的行切片向量，由 [`eachrow`](@ref) 构造。

可以使用 [`parent`](@ref) 获取底层矩阵。
