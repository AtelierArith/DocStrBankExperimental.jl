```
eachindex(A...)
eachindex(::IndexStyle, A::AbstractArray...)
```

创建一个可迭代对象，以高效的方式访问 `AbstractArray` `A` 的每个索引。对于选择快速线性索引的数组类型（如 `Array`），这仅仅是范围 `1:length(A)`，如果它们使用的是基于1的索引。对于未选择快速线性索引的数组类型，通常返回一个专门的笛卡尔范围，以便使用为每个维度指定的索引高效地索引数组。

一般来说，`eachindex` 接受任意可迭代对象，包括字符串和字典，并返回一个支持任意索引类型（例如不均匀间隔或非整数索引）的迭代器对象。

如果 `A` 是 `AbstractArray`，可以通过将一个具有 `IndexStyle` 类型的值作为第一个参数显式指定 `eachindex` 应返回的索引样式（通常如果需要线性索引则为 `IndexLinear()`，如果想要笛卡尔范围则为 `IndexCartesian()`）。

如果您提供多个 `AbstractArray` 参数，`eachindex` 将创建一个对所有参数都快速的可迭代对象（通常如果所有输入都有快速线性索引，则为 [`UnitRange`](@ref)，否则为 [`CartesianIndices`](@ref)）。如果数组的大小和/或维度不同，将抛出 `DimensionMismatch` 异常。

另请参见 [`pairs`](@ref)`(A)` 以同时迭代索引和值，以及 [`axes`](@ref)`(A, 2)` 以获取沿一个维度的有效索引。

# 示例

```jldoctest
julia> A = [10 20; 30 40];

julia> for i in eachindex(A) # 线性索引
           println("A[", i, "] == ", A[i])
       end
A[1] == 10
A[2] == 30
A[3] == 20
A[4] == 40

julia> for i in eachindex(view(A, 1:2, 1:1)) # 笛卡尔索引
           println(i)
       end
CartesianIndex(1, 1)
CartesianIndex(2, 1)
```
