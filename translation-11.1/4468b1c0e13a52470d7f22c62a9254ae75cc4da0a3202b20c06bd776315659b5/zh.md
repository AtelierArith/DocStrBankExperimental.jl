```
rdiv!(A::AbstractArray, b::Number)
```

将数组 `A` 中的每个条目除以标量 `b`，并就地覆盖 `A`。使用 [`ldiv!`](@ref) 从左侧除以标量。

# 示例

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> rdiv!(A, 2.0)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
