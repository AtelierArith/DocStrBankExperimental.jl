```
==(a::AbstractString, b::AbstractString) -> Bool
```

测试两个字符串是否逐字符相等（从技术上讲，是逐Unicode代码点相等）。如果任一字符串是[`AnnotatedString`](@ref)，则字符串属性也必须匹配。

# 示例

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
