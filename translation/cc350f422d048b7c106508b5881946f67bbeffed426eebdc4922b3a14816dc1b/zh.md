```
lstrip([pred=isspace,] str::AbstractString) -> SubString
lstrip(str::AbstractString, chars) -> SubString
```

从 `str` 中移除前导字符，可以是由 `chars` 指定的字符，或者是 `pred` 函数返回 `true` 的字符。

默认行为是移除前导空白和分隔符：有关详细信息，请参见 [`isspace`](@ref)。

可选的 `chars` 参数指定要移除的字符：它可以是单个字符，或字符的向量或集合。

另请参见 [`strip`](@ref) 和 [`rstrip`](@ref)。

# 示例

```jldoctest
julia> a = lpad("March", 20)
"               March"

julia> lstrip(a)
"March"
```
