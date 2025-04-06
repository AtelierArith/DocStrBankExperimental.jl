```
zeros([T=Float64,] dims::Tuple)
zeros([T=Float64,] dims...)
```

创建一个元素类型为 `T` 的数组，所有元素为零，大小由 `dims` 指定。另见 [`fill`](@ref), [`ones`](@ref), [`zero`](@ref)。

# 示例

```jldoctest
julia> zeros(1)
1-element Vector{Float64}:
 0.0

julia> zeros(Int8, 2, 3)
2×3 Matrix{Int8}:
 0  0  0
 0  0  0
```
