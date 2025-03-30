```
isspace(c::AbstractChar) -> Bool
```

测试一个字符是否是任何空白字符。包括 ASCII 字符 '\t'、'\n'、'\v'、'\f'、'\r' 和 ' '，拉丁-1 字符 U+0085，以及 Unicode 类别 Zs 中的字符。

# 示例

```jldoctest
julia> isspace('\n')
true

julia> isspace('\r')
true

julia> isspace(' ')
true

julia> isspace('\x20')
true
```
