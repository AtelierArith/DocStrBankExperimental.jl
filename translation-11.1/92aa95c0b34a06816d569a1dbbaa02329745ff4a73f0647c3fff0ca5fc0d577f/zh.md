```
lowercase(s::AbstractString)
```

返回 `s`，将所有字符转换为小写。

另见 [`uppercase`](@ref)，[`titlecase`](@ref)，[`lowercasefirst`](@ref)。

# 示例

```jldoctest
julia> lowercase("STRINGS AND THINGS")
"strings and things"
```
