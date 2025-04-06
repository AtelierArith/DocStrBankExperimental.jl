```
repeat(c::AbstractChar, r::Integer) -> String
```

将字符重复 `r` 次。这可以通过调用 [`c^r`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)) 来等效实现。

# 示例

```jldoctest
julia> repeat('A', 3)
"AAA"
```
