```
transcode(T, src)
```

在Unicode编码之间转换字符串数据。`src`可以是`String`或UTF-XX代码单元的`Vector{UIntXX}`，其中`XX`为8、16或32。`T`表示返回值的编码：`String`返回一个（UTF-8编码的）`String`，或`UIntXX`返回一个UTF-`XX`数据的`Vector{UIntXX}`。（别名[`Cwchar_t`](@ref)也可以用作整数类型，用于转换外部C库使用的`wchar_t*`字符串。）

只要输入数据可以合理地表示为目标编码，`transcode`函数就会成功；即使对于无效的Unicode数据，它在UTF-XX编码之间的转换也总是成功。

目前仅支持与UTF-8的转换。

# 示例

```jldoctest
julia> str = "αβγ"
"αβγ"

julia> transcode(UInt16, str)
3-element Vector{UInt16}:
 0x03b1
 0x03b2
 0x03b3

julia> transcode(String, transcode(UInt16, str))
"αβγ"
```
