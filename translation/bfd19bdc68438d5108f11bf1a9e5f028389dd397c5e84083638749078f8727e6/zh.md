```
widemul(x, y)
```

将 `x` 和 `y` 相乘，结果为更大的类型。

另见 [`promote`](@ref), [`Base.add_sum`](@ref).

# 示例

```jldoctest
julia> widemul(Float32(3.0), 4.0) isa BigFloat
true

julia> typemax(Int8) * typemax(Int8)
1

julia> widemul(typemax(Int8), typemax(Int8))  # == 127^2
16129
```
