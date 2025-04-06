```
ldiv!(a::Number, B::AbstractArray)
```

将数组 `B` 中的每个条目除以标量 `a`，并就地覆盖 `B`。使用 [`rdiv!`](@ref) 从右侧除以标量。

# 示例

```jldoctest
julia> B = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> ldiv!(2.0, B)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
