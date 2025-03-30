```
searchsorted(v, x; by=identity, lt=isless, rev=false)
```

返回在 `v` 中与 `x` 等值的索引范围，如果 `v` 不包含与 `x` 等值的元素，则返回位于插入点的空范围。向量 `v` 必须根据关键字定义的顺序进行排序。有关关键字的含义和等值的定义，请参阅 [`sort!`](@ref)。请注意，`by` 函数应用于被搜索的值 `x` 以及 `v` 中的值。

该范围通常使用二分搜索找到，但对于某些输入有优化的实现。

另请参见：[`searchsortedfirst`](@ref)，[`sort!`](@ref)，[`insorted`](@ref)，[`findall`](@ref)。

# 示例

```jldoctest
julia> searchsorted([1, 2, 4, 5, 5, 7], 4) # 单个匹配
3:3

julia> searchsorted([1, 2, 4, 5, 5, 7], 5) # 多个匹配
4:5

julia> searchsorted([1, 2, 4, 5, 5, 7], 3) # 无匹配，在中间插入
3:2

julia> searchsorted([1, 2, 4, 5, 5, 7], 9) # 无匹配，在末尾插入
7:6

julia> searchsorted([1, 2, 4, 5, 5, 7], 0) # 无匹配，在开头插入
1:0

julia> searchsorted([1=>"one", 2=>"two", 2=>"two", 4=>"four"], 2=>"two", by=first) # 比较对的键
2:3
```
