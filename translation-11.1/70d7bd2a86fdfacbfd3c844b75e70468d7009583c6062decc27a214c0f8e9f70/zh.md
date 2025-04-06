```
prevind(A, i)
```

返回 `A` 中 `i` 之前的索引。返回的索引通常等于整数 `i - 1`。此函数对于通用代码可能很有用。

!!! warning
    返回的索引可能超出范围。考虑使用 [`checkbounds`](@ref)。


另请参见：[`nextind`](@ref)。

# 示例

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prevind(x, 4) # 有效结果
3

julia> prevind(x, 1) # 无效结果
0

julia> prevind(x, CartesianIndex(2, 2)) # 有效结果
CartesianIndex(1, 2)

julia> prevind(x, CartesianIndex(1, 1)) # 无效结果
CartesianIndex(2, 0)
```
