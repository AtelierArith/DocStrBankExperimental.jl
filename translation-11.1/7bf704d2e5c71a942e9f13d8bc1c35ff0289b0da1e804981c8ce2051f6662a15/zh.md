```
rmul!(A::AbstractArray, b::Number)
```

通过标量 `b` 缩放数组 `A`，并就地覆盖 `A`。使用 [`lmul!`](@ref) 从左侧乘以标量。缩放操作遵循 `A` 的元素与 `b` 之间的乘法 [`*`](@ref) 的语义。特别地，这也适用于涉及非有限数的乘法，例如 `NaN` 和 `±Inf`。

!!! compat "Julia 1.1"
    在 Julia 1.1 之前，`A` 中的 `NaN` 和 `±Inf` 条目处理不一致。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rmul!(A, 2)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> rmul!([NaN], 0.0)
1-element Vector{Float64}:
 NaN
```
