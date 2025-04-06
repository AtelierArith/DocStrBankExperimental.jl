```
keys(a::AbstractArray)
```

返回一个有效索引的高效数组，描述 `a` 的所有有效索引，并按照 `a` 本身的形状排列。

一维数组（向量）的键是整数，而所有其他 N 维数组使用 [`CartesianIndex`](@ref) 来描述它们的位置。通常，特殊数组类型 [`LinearIndices`](@ref) 和 [`CartesianIndices`](@ref) 被用来高效地表示这些整数和 `CartesianIndex` 的数组。

请注意，数组的 `keys` 可能不是最有效的索引类型；为了获得最佳性能，请使用 [`eachindex`](@ref) 替代。

# 示例

```jldoctest
julia> keys([4, 5, 6])
3-element LinearIndices{1, Tuple{Base.OneTo{Int64}}}:
 1
 2
 3

julia> keys([4 5; 6 7])
CartesianIndices((2, 2))
```
