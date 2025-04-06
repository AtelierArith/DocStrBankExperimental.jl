```
vec(a::AbstractArray) -> AbstractVector
```

将数组 `a` 重新形状为一维列向量。如果 `a` 已经是 `AbstractVector`，则返回 `a`。结果数组与 `a` 共享相同的底层数据，因此只有在 `a` 是可变的情况下才会是可变的，在这种情况下，修改一个也会修改另一个。

# 示例

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> vec(a)
6-element Vector{Int64}:
 1
 4
 2
 5
 3
 6

julia> vec(1:3)
1:3
```

另请参见 [`reshape`](@ref), [`dropdims`](@ref).
