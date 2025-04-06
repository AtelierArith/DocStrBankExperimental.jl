```
axpy!(α, x::AbstractArray, y::AbstractArray)
```

用 `x * α + y` 覆盖 `y` 并返回 `y`。如果 `x` 和 `y` 具有相同的轴，则等价于 `y .+= x .* a`。

# 示例

```jldoctest
julia> x = [1; 2; 3];

julia> y = [4; 5; 6];

julia> axpy!(2, x, y)
3-element Vector{Int64}:
  6
  9
 12
```
