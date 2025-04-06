```
chopprefix(s::AbstractString, prefix::Union{AbstractString,Regex}) -> SubString
```

从 `s` 中移除前缀 `prefix`。如果 `s` 不以 `prefix` 开头，则返回一个与 `s` 相等的字符串。

另见 [`chopsuffix`](@ref)。

!!! compat "Julia 1.8"
    此函数自 Julia 1.8 起可用。


# 示例

```jldoctest
julia> chopprefix("Hamburger", "Ham")
"burger"

julia> chopprefix("Hamburger", "hotdog")
"Hamburger"
```
