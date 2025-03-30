```
axpby!(α, x::AbstractArray, β, y::AbstractArray)
```

用 `x * α + y * β` 覆盖 `y` 并返回 `y`。如果 `x` 和 `y` 具有相同的轴，则等价于 `y .= x .* a .+ y .* β`。

# 示例

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpby!(2, x, 2, y)
3-element Vector{Int64}:
 10
 14
 18
```
