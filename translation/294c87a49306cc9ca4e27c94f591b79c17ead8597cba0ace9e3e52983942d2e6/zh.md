```
lowercase(c::AbstractChar)
```

将 `c` 转换为小写。

另见 [`uppercase`](@ref), [`titlecase`](@ref)。

# 示例

```jldoctest
julia> lowercase('A')
'a': ASCII/Unicode U+0061 (类别 Ll: 字母, 小写)

julia> lowercase('Ö')
'ö': Unicode U+00F6 (类别 Ll: 字母, 小写)
```
