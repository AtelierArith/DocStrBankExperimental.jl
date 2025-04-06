```
chomp(s::AbstractString) -> SubString
```

从字符串中移除一个尾随换行符。

另见 [`chop`](@ref)。

# 示例

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
