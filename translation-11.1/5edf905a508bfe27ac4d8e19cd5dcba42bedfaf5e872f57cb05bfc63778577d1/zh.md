```
ispow2(n::Number) -> Bool
```

测试 `n` 是否为整数的二次幂。

另见 [`count_ones`](@ref), [`prevpow`](@ref), [`nextpow`](@ref)。

# 示例

```jldoctest
julia> ispow2(4)
true

julia> ispow2(5)
false

julia> ispow2(4.5)
false

julia> ispow2(0.25)
true

julia> ispow2(1//8)
true
```

!!! compat "Julia 1.6"
    在 Julia 1.6 中添加了对非 `Integer` 参数的支持。

