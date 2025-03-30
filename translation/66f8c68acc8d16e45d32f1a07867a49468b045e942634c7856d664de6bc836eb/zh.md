```
UnitRange{T<:Real}
```

一个由类型 `T` 的 `start` 和 `stop` 参数化的范围，填充了从 `start` 开始到超过 `stop` 的元素，元素之间间隔为 `1`。语法 `a:b`，其中 `a` 和 `b` 都是 `Integer`，会创建一个 `UnitRange`。

# 示例

```jldoctest
julia> collect(UnitRange(2.3, 5.2))
3-element Vector{Float64}:
 2.3
 3.3
 4.3

julia> typeof(1:10)
UnitRange{Int64}
```
