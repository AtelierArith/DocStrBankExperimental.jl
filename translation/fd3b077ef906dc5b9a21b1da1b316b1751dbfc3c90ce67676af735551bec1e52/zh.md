```
zero(x)
zero(::Type)
```

获取类型 `x` 的加法单位元素（`x` 也可以指定类型本身）。

另见 [`iszero`](@ref), [`one`](@ref), [`oneunit`](@ref), [`oftype`](@ref).

# 示例

```jldoctest
julia> zero(1)
0

julia> zero(big"2.0")
0.0

julia> zero(rand(2,2))
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
