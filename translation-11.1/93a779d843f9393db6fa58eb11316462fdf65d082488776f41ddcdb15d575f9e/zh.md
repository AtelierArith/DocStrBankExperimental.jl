```
lastindex(collection) -> 整数
lastindex(collection, d) -> 整数
```

返回 `collection` 的最后一个索引。如果给定 `d`，则返回沿维度 `d` 的 `collection` 的最后一个索引。

语法 `A[end]` 和 `A[end, end]` 分别简化为 `A[lastindex(A)]` 和 `A[lastindex(A, 1), lastindex(A, 2)]`。

另请参见: [`axes`](@ref), [`firstindex`](@ref), [`eachindex`](@ref), [`prevind`](@ref)。

# 示例

```jldoctest
julia> lastindex([1,2,4])
3

julia> lastindex(rand(3,4,5), 2)
4
```
