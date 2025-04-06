```
SubString(s::AbstractString, i::Integer, j::Integer=lastindex(s))
SubString(s::AbstractString, r::UnitRange{<:Integer})
```

像 [`getindex`](@ref) 一样，但返回父字符串 `s` 在范围 `i:j` 或 `r` 内的视图，而不是创建副本。

[`@views`](@ref) 宏将任何字符串切片 `s[i:j]` 转换为子字符串 `SubString(s, i, j)` 在代码块中。

# 示例

```jldoctest
julia> SubString("abc", 1, 2)
"ab"

julia> SubString("abc", 1:2)
"ab"

julia> SubString("abc", 2)
"bc"
```
