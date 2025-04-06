```
isprint(c::AbstractChar) -> Bool
```

测试一个字符是否可打印，包括空格，但不包括控制字符。

# 示例

```jldoctest
julia> isprint('\x01')
false

julia> isprint('A')
true
```
