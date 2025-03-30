```
isdigit(c::AbstractChar) -> Bool
```

测试一个字符是否为十进制数字（0-9）。

另见：[`isletter`](@ref)。

# 示例

```jldoctest
julia> isdigit('❤')
false

julia> isdigit('9')
true

julia> isdigit('α')
false
```
