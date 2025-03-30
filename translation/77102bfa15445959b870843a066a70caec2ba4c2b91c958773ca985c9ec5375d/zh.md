```
lmul!(a::Number, B::AbstractArray)
```

通过标量 `a` 缩放数组 `B`，并就地覆盖 `B`。使用 [`rmul!`](@ref) 从右侧乘以标量。缩放操作遵循 `a` 与 `B` 中元素之间的乘法 [`*`](@ref) 语义。特别地，这也适用于涉及非有限数的乘法，例如 `NaN` 和 `±Inf`。

!!! compat "Julia 1.1"
    在 Julia 1.1 之前，`B` 中的 `NaN` 和 `±Inf` 条目处理不一致。


# 示例

```jldoctest
julia> B = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> lmul!(2, B)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> lmul!(0.0, [Inf])
1-element Vector{Float64}:
 NaN
```
