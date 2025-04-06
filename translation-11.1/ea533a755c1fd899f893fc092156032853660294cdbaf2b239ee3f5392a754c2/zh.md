```
floatmax(T = Float64)
```

返回浮点类型 `T` 可表示的最大有限数。

另见: [`typemax`](@ref), [`floatmin`](@ref), [`eps`](@ref)。

# 示例

```jldoctest
julia> floatmax(Float16)
Float16(6.55e4)

julia> floatmax(Float32)
3.4028235f38

julia> floatmax()
1.7976931348623157e308

julia> typemax(Float64)
Inf
```
