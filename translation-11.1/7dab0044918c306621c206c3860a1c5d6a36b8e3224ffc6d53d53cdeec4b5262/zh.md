```
uppercase(c::AbstractChar)
```

将 `c` 转换为大写。

另见 [`lowercase`](@ref), [`titlecase`](@ref)。

# 示例

```jldoctest
julia> uppercase('a')
'A': ASCII/Unicode U+0041 (类别 Lu: 字母，大写)

julia> uppercase('ê')
'Ê': Unicode U+00CA (类别 Lu: 字母，大写)
```
