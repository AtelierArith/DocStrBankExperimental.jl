```
rem(x, y)
%(x, y)
```

欧几里得除法的余数，返回与 `x` 同符号且绝对值小于 `y` 的值。该值始终是精确的。

另见: [`div`](@ref), [`mod`](@ref), [`mod1`](@ref), [`divrem`](@ref).

# 示例

```jldoctest
julia> x = 15; y = 4;

julia> x % y
3

julia> x == div(x, y) * y + rem(x, y)
true

julia> rem.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -2  -1  0  -2  -1  0  1  2  0  1  2
```
