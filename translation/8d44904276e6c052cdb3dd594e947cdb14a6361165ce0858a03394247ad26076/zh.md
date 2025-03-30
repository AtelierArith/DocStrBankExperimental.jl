```
chop(s::AbstractString; head::Integer = 0, tail::Integer = 1)
```

从`s`中移除前`head`个字符和后`tail`个字符。调用`chop(s)`会移除`s`的最后一个字符。如果请求移除的字符数量超过了`length(s)`，则返回一个空字符串。

另请参见 [`chomp`](@ref), [`startswith`](@ref), [`first`](@ref).

# 示例

```jldoctest
julia> a = "March"
"March"

julia> chop(a)
"Marc"

julia> chop(a, head = 1, tail = 2)
"ar"

julia> chop(a, head = 5, tail = 5)
""
```
