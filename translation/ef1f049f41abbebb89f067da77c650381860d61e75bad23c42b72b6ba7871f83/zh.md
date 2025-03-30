```
@raw_str -> String
```

创建一个不进行插值和反转义的原始字符串。例外的是，双引号仍然必须被转义。反斜杠同时转义双引号和其他反斜杠，但仅当一系列反斜杠在引号字符之前时。因此，2n个反斜杠后跟一个引号编码n个反斜杠和字面量的结束，而2n+1个反斜杠后跟一个引号编码n个反斜杠后跟一个引号字符。

# 示例

```jldoctest
julia> println(raw"\ $x")
\ $x

julia> println(raw"\"")
"

julia> println(raw"\\\"")
\"

julia> println(raw"\\x \\\"")
\\x \"
```
