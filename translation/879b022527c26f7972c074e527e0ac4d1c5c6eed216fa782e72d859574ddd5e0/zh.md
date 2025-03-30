```
eachmatch(r::Regex, s::AbstractString; overlap::Bool=false)
```

搜索正则表达式 `r` 在 `s` 中的所有匹配项，并返回一个匹配项的迭代器。如果 `overlap` 为 `true`，则允许匹配序列在原始字符串中重叠索引，否则它们必须来自不同的字符范围。

# 示例

```jldoctest
julia> rx = r"a.a"
r"a.a"

julia> m = eachmatch(rx, "a1a2a3a")
Base.RegexMatchIterator{String}(r"a.a", "a1a2a3a", false)

julia> collect(m)
2-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a3a")

julia> collect(eachmatch(rx, "a1a2a3a", overlap = true))
3-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a2a")
 RegexMatch("a3a")
```
