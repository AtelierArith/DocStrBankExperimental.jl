```
isxdigit(c::AbstractChar) -> Bool
```

测试一个字符是否是有效的十六进制数字。请注意，这不包括 `x`（如标准的 `0x` 前缀）。

# 示例

```jldoctest
julia> isxdigit('a')
true

julia> isxdigit('x')
false
```
