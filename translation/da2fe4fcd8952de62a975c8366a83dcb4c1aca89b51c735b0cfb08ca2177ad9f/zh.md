```
chopsuffix(s::AbstractString, suffix::Union{AbstractString,Regex}) -> SubString
```

从 `s` 中移除后缀 `suffix`。如果 `s` 不以 `suffix` 结尾，则返回一个与 `s` 相等的字符串。

另见 [`chopprefix`](@ref)。

!!! compat "Julia 1.8"
    此函数自 Julia 1.8 起可用。


# 示例

```jldoctest
julia> chopsuffix("Hamburger", "er")
"Hamburg"

julia> chopsuffix("Hamburger", "hotdog")
"Hamburger"
```
