```
push!(collection, items...) -> collection
```

将一个或多个 `items` 插入到 `collection` 中。如果 `collection` 是一个有序容器，项目将按给定顺序插入到末尾。

# 示例

```jldoctest
julia> push!([1, 2, 3], 4, 5, 6)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

如果 `collection` 是有序的，使用 [`append!`](@ref) 将另一个集合的所有元素添加到其中。前面示例的结果等同于 `append!([1, 2, 3], [4, 5, 6])`。对于 `AbstractSet` 对象，可以使用 [`union!`](@ref)。

有关性能模型的说明，请参见 [`sizehint!`](@ref)。

另请参见 [`pushfirst!`](@ref)。
