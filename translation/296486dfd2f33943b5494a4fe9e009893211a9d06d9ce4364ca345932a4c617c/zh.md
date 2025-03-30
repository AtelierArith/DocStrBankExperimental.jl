```
LinearIndices(A::AbstractArray)
```

返回一个与 `A` 具有相同形状和 [`axes`](@ref) 的 `LinearIndices` 数组，保存 `A` 中每个条目的线性索引。使用笛卡尔索引对该数组进行索引可以将其映射到线性索引。

对于常规索引的数组（索引从 1 开始）或任何多维数组，线性索引的范围是从 1 到 `length(A)`。然而，对于 `AbstractVector`，线性索引是 `axes(A, 1)`，因此对于具有非常规索引的向量，线性索引并不从 1 开始。

调用此函数是编写利用线性索引的算法的“安全”方式。

# 示例

```jldoctest
julia> A = fill(1, (5,6,7));

julia> b = LinearIndices(A);

julia> extrema(b)
(1, 210)
```

```
LinearIndices(inds::CartesianIndices) -> R
LinearIndices(sz::Dims) -> R
LinearIndices((istart:istop, jstart:jstop, ...)) -> R
```

返回一个具有指定形状或 [`axes`](@ref) 的 `LinearIndices` 数组。

# 示例

此构造函数的主要目的是直观地将笛卡尔索引转换为线性索引：

```jldoctest
julia> linear = LinearIndices((1:3, 1:2))
3×2 LinearIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 1  4
 2  5
 3  6

julia> linear[1,2]
4
```
