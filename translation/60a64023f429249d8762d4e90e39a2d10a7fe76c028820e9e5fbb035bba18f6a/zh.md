```
titlecase(c::AbstractChar)
```

将 `c` 转换为标题大小写。这可能与双音字母的大写形式不同，请参见下面的示例。

另请参阅 [`uppercase`](@ref), [`lowercase`](@ref).

# 示例

```jldoctest
julia> titlecase('a')
'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)

julia> titlecase('ǆ')
'ǅ': Unicode U+01C5 (category Lt: Letter, titlecase)

julia> uppercase('ǆ')
'Ǆ': Unicode U+01C4 (category Lu: Letter, uppercase)
```
