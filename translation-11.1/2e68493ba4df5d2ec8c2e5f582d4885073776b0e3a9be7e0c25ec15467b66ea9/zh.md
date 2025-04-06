```
getindex(collection, key...)
```

在集合中检索存储在给定键或索引处的值。语法 `a[i,j,...]` 被编译器转换为 `getindex(a, i, j, ...)`。

另请参见 [`get`](@ref), [`keys`](@ref), [`eachindex`](@ref)。

# 示例

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> getindex(A, "a")
1
```
