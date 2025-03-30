```
occursin(needle::Union{AbstractString,AbstractPattern,AbstractChar}, haystack::AbstractString)
```

确定第一个参数是否是第二个参数的子字符串。如果 `needle` 是正则表达式，则检查 `haystack` 是否包含匹配项。

# 示例

```jldoctest
julia> occursin("Julia", "JuliaLang is pretty cool!")
true

julia> occursin('a', "JuliaLang is pretty cool!")
true

julia> occursin(r"a.a", "aba")
true

julia> occursin(r"a.a", "abba")
false
```

另见 [`contains`](@ref).
