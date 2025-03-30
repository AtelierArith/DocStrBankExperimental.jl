```
nextind(A, i)
```

返回 `A` 中 `i` 之后的索引。返回的索引通常等于整数 `i + 1`。此函数对于通用代码非常有用。

!!! warning
    返回的索引可能超出边界。考虑使用 [`checkbounds`](@ref)。


另见: [`prevind`](@ref)。

# 示例

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nextind(x, 1) # 有效结果
2

julia> nextind(x, 4) # 无效结果
5

julia> nextind(x, CartesianIndex(1, 1)) # 有效结果
CartesianIndex(2, 1)

julia> nextind(x, CartesianIndex(2, 2)) # 无效结果
CartesianIndex(1, 3)
```
