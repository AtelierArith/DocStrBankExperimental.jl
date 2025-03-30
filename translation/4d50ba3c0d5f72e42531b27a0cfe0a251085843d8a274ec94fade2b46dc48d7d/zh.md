```
selectdim(A, d::Integer, i)
```

返回 `A` 的所有数据的视图，其中维度 `d` 的索引等于 `i`。

等价于 `view(A,:,:,...,i,:,:,...)`，其中 `i` 位于位置 `d`。

另见: [`eachslice`](@ref)。

# 示例

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8]
2×4 Matrix{Int64}:
 1  2  3  4
 5  6  7  8

julia> selectdim(A, 2, 3)
2-element view(::Matrix{Int64}, :, 3) with eltype Int64:
 3
 7

julia> selectdim(A, 2, 3:4)
2×2 view(::Matrix{Int64}, :, 3:4) with eltype Int64:
 3  4
 7  8
```
