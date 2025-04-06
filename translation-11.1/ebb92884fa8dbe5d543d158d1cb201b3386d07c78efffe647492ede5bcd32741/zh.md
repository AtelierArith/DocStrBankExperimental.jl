```
match(r::Regex, s::AbstractString[, idx::Integer[, addopts]])
```

在字符串 `s` 中搜索正则表达式 `r` 的第一个匹配，并返回一个 [`RegexMatch`](@ref) 对象，其中包含匹配项，如果匹配失败则返回 nothing。可以通过访问 `m.match` 来检索匹配的子字符串，通过访问 `m.captures` 来检索捕获的序列。可选的 `idx` 参数指定开始搜索的索引。

# 示例

```jldoctest
julia> rx = r"a(.)a"
r"a(.)a"

julia> m = match(rx, "cabac")
RegexMatch("aba", 1="b")

julia> m.captures
1-element Vector{Union{Nothing, SubString{String}}}:
 "b"

julia> m.match
"aba"

julia> match(rx, "cabac", 3) === nothing
true
```
