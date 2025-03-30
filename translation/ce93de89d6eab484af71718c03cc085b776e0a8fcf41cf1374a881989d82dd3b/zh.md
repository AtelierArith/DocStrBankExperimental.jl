```
endswith(s::AbstractString, suffix::Regex)
```

如果 `s` 以正则表达式模式 `suffix` 结尾，则返回 `true`。

!!! note
    `endswith` 不会将锚点编译到正则表达式中，而是将锚点作为 `match_option` 传递给 PCRE。如果编译时间被摊销，`occursin(r"...$", s)` 比 `endswith(s, r"...")` 更快。


另请参见 [`occursin`](@ref) 和 [`startswith`](@ref)。

!!! compat "Julia 1.2"
    此方法至少需要 Julia 1.2。


# 示例

```jldoctest
julia> endswith("JuliaLang", r"Lang|Roberts")
true
```
