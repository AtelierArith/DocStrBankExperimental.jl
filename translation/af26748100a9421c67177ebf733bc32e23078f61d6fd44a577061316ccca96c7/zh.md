```
getindex(type[, elements...])
```

构造指定类型的一维数组。通常使用语法 `Type[]` 调用。元素值可以使用 `Type[a,b,c,...]` 指定。

# 示例

```jldoctest
julia> Int8[1, 2, 3]
3-element Vector{Int8}:
 1
 2
 3

julia> getindex(Int8, 1, 2, 3)
3-element Vector{Int8}:
 1
 2
 3
```
