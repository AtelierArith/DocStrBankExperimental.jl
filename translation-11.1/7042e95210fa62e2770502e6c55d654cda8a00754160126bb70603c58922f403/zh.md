```
length(collection) -> 整数
```

返回集合中元素的数量。

使用 [`lastindex`](@ref) 获取可索引集合的最后一个有效索引。

另请参见：[`size`](@ref)，[`ndims`](@ref)，[`eachindex`](@ref)。

# 示例

```jldoctest
julia> length(1:5)
5

julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
