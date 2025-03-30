```
insorted(x, v; by=identity, lt=isless, rev=false) -> Bool
```

确定向量 `v` 是否包含与 `x` 等价的任何值。向量 `v` 必须根据关键字定义的顺序进行排序。有关关键字的含义和等价的定义，请参阅 [`sort!`](@ref)。请注意，`by` 函数应用于被搜索的值 `x` 以及 `v` 中的值。

检查通常使用二分搜索进行，但对于某些输入有优化的实现。

另请参见 [`in`](@ref)。

# 示例

```jldoctest
julia> insorted(4, [1, 2, 4, 5, 5, 7]) # 单个匹配
true

julia> insorted(5, [1, 2, 4, 5, 5, 7]) # 多个匹配
true

julia> insorted(3, [1, 2, 4, 5, 5, 7]) # 无匹配
false

julia> insorted(9, [1, 2, 4, 5, 5, 7]) # 无匹配
false

julia> insorted(0, [1, 2, 4, 5, 5, 7]) # 无匹配
false

julia> insorted(2=>"TWO", [1=>"one", 2=>"two", 4=>"four"], by=first) # 比较对的键
true
```

!!! compat "Julia 1.6"
    `insorted` 在 Julia 1.6 中添加。

