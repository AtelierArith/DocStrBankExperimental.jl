```
insert!(a::Vector, index::Integer, item)
```

在给定的 `index` 处将 `item` 插入到 `a` 中。`index` 是 `item` 在结果 `a` 中的索引。

另请参见：[`push!`](@ref), [`replace`](@ref), [`popat!`](@ref), [`splice!`](@ref)。

# 示例

```jldoctest
julia> insert!(Any[1:6;], 3, "here")
7-element Vector{Any}:
 1
 2
  "here"
 3
 4
 5
 6
```
