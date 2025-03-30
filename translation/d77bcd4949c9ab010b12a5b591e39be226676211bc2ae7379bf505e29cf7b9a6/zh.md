```
repeat(s::AbstractString, r::Integer)
```

将字符串重复 `r` 次。这可以写成 `s^r`。

另见 [`^`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer))。

# 示例

```jldoctest
julia> repeat("ha", 3)
"hahaha"
```
