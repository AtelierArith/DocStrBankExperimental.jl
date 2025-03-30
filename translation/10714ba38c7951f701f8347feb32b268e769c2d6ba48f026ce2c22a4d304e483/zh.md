```
isvalid(T, value) -> Bool
```

如果给定的值对于该类型是有效的，则返回 `true`。当前类型可以是 `AbstractChar` 或 `String`。`AbstractChar` 的值可以是 `AbstractChar` 类型或 [`UInt32`](@ref)。`String` 的值可以是该类型、`SubString{String}`、`Vector{UInt8}` 或其连续子数组。

# 示例

```jldoctest
julia> isvalid(Char, 0xd800)
false

julia> isvalid(String, SubString("thisisvalid",1,5))
true

julia> isvalid(Char, 0xd799)
true
```

!!! compat "Julia 1.6"
    在 Julia 1.6 中添加了对子数组值的支持。

