```
append!(collection, collections...) -> collection.
```

对于有序容器 `collection`，将每个 `collections` 的元素添加到其末尾。

!!! compat "Julia 1.6"
    指定多个要附加的集合需要至少 Julia 1.6。


# 示例

```jldoctest
julia> append!([1], [2, 3])
3-element Vector{Int64}:
 1
 2
 3

julia> append!([1, 2, 3], [4, 5], [6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

使用 [`push!`](@ref) 将单个项目添加到 `collection` 中，这些项目本身不在另一个集合中。前面示例的结果等同于 `push!([1, 2, 3], 4, 5, 6)`。

有关性能模型的说明，请参见 [`sizehint!`](@ref)。

另请参阅 [`vcat`](@ref) 用于向量，[`union!`](@ref) 用于集合，以及 [`prepend!`](@ref) 和 [`pushfirst!`](@ref) 用于相反的顺序。
