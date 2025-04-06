```
searchsortedlast(v, x; by=identity, lt=isless, rev=false)
```

返回 `v` 中最后一个不在 `x` 之后的值的索引。如果 `v` 中的所有值都在 `x` 之后，则返回 `firstindex(v) - 1`。

向量 `v` 必须根据关键字定义的顺序进行排序。在返回的索引后立即 `insert!` `x` 将保持排序顺序。有关关键字的含义和使用，请参阅 [`sort!`](@ref)。请注意，`by` 函数应用于被搜索的值 `x` 以及 `v` 中的值。

索引通常使用二分搜索找到，但对于某些输入有优化的实现。

# 示例

```jldoctest
julia> searchsortedlast([1, 2, 4, 5, 5, 7], 4) # 单个匹配
3

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 5) # 多个匹配
5

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 3) # 无匹配，在中间插入
2

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 9) # 无匹配，在末尾插入
6

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 0) # 无匹配，在开始插入
0

julia> searchsortedlast([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # 比较对的键
2
```
