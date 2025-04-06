```
Slices{P,SM,AX,S,N} <: AbstractSlices{S,N}
```

一个 `AbstractArray`，用于在指定维度上对父数组进行切片，返回从其他维度选择所有数据的视图。

这些通常应通过 [`eachslice`](@ref)、[`eachcol`](@ref) 或 [`eachrow`](@ref) 构造。

[`parent(s::Slices)`](@ref) 将返回父数组。
