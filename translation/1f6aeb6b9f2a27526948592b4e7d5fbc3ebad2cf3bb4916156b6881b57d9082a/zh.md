```
firstindex(collection) -> 整数
firstindex(collection, d) -> 整数
```

返回 `collection` 的第一个索引。如果给定 `d`，则返回沿维度 `d` 的 `collection` 的第一个索引。

语法 `A[begin]` 和 `A[1, begin]` 分别降级为 `A[firstindex(A)]` 和 `A[1, firstindex(A, 2)]`。

另请参见: [`first`](@ref), [`axes`](@ref), [`lastindex`](@ref), [`nextind`](@ref)。

# 示例

```jldoctest
julia> firstindex([1,2,4])
1

julia> firstindex(rand(3,4,5), 2)
1
```
