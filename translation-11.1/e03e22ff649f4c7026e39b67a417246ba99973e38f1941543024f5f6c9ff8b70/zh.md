```
rstrip([pred=isspace,] str::AbstractString) -> SubString
rstrip(str::AbstractString, chars) -> SubString
```

从 `str` 中移除尾部字符，可以是由 `chars` 指定的字符，或者是函数 `pred` 返回 `true` 的字符。

默认行为是移除尾部的空白和分隔符：有关详细信息，请参见 [`isspace`](@ref)。

可选的 `chars` 参数指定要移除的字符：它可以是单个字符，或字符的向量或集合。

另请参见 [`strip`](@ref) 和 [`lstrip`](@ref)。

# 示例

```jldoctest
julia> a = rpad("March", 20)
"March               "

julia> rstrip(a)
"March"
```
