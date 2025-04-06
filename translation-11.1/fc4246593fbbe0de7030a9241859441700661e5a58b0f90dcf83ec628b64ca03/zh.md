```
lpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

将 `s` 转换为字符串，并用 `p` 在左侧填充结果字符串，使其长度为 `n` 个字符（在 [`textwidth`](@ref) 中）。如果 `s` 已经是 `n` 个字符长，则返回相等的字符串。默认情况下用空格填充。

# 示例

```jldoctest
julia> lpad("March", 10)
"     March"
```

!!! compat "Julia 1.7"
    在 Julia 1.7 中，此函数已更改为使用 `textwidth` 而不是原始字符（代码点）计数。

