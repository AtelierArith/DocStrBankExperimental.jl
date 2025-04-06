```
BoundsError([a],[i])
```

对数组 `a` 的索引操作尝试访问索引 `i` 的越界元素。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> A = fill(1.0, 7);

julia> A[8]
错误: BoundsError: 尝试访问 7-element Vector{Float64} 的索引 [8]


julia> B = fill(1.0, (2,3));

julia> B[2, 4]
错误: BoundsError: 尝试访问 2×3 Matrix{Float64} 的索引 [2, 4]


julia> B[9]
错误: BoundsError: 尝试访问 2×3 Matrix{Float64} 的索引 [9]

```
