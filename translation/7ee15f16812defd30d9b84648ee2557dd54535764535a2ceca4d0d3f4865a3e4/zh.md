```
clamp(x, lo, hi)
```

如果 `lo <= x <= hi`，则返回 `x`。如果 `x > hi`，则返回 `hi`。如果 `x < lo`，则返回 `lo`。参数会提升到一个共同的类型。

另见 [`clamp!`](@ref), [`min`](@ref), [`max`](@ref)。

!!! compat "Julia 1.3"
    `missing` 作为第一个参数需要至少 Julia 1.3。


# 示例

```jldoctest
julia> clamp.([pi, 1.0, big(10)], 2.0, 9.0)
3-element Vector{BigFloat}:
 3.141592653589793238462643383279502884197169399375105820974944592307816406286198
 2.0
 9.0

julia> clamp.([11, 8, 5], 10, 6)  # 一个 lo > hi 的例子
3-element Vector{Int64}:
  6
  6
 10
```
