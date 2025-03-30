```
collect(element_type, collection)
```

返回一个具有给定元素类型的 `Array`，包含集合或可迭代对象中的所有项。结果具有与 `collection` 相同的形状和维度数量。

# 示例

```jldoctest
julia> collect(Float64, 1:2:5)
3-element Vector{Float64}:
 1.0
 3.0
 5.0
```
