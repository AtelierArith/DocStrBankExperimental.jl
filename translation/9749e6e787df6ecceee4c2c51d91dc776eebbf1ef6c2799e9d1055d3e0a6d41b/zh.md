```
cld(x, y)
```

大于或等于 `x / y` 的最小整数。等价于 `div(x, y, RoundUp)`。

另见 [`div`](@ref), [`fld`](@ref)。

# 示例

```jldoctest
julia> cld(5.5, 2.2)
3.0

julia> cld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  1  1  1  2  2
```
