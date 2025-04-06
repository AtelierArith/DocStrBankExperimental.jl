```
count(
    pattern::Union{AbstractChar,AbstractString,AbstractPattern},
    string::AbstractString;
    overlap::Bool = false,
)
```

返回 `pattern` 在 `string` 中匹配的数量。这相当于调用 `length(findall(pattern, string))`，但更高效。

如果 `overlap=true`，则匹配的序列可以在原始字符串中重叠索引，否则它们必须来自不相交的字符范围。

!!! compat "Julia 1.3"
    此方法至少需要 Julia 1.3。


!!! compat "Julia 1.7"
    将字符用作模式至少需要 Julia 1.7。


# 示例

```jldoctest
julia> count('a', "JuliaLang")
2

julia> count(r"a(.)a", "cabacabac", overlap=true)
3

julia> count(r"a(.)a", "cabacabac")
2
```
