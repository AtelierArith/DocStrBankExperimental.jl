```
escape_string(str::AbstractString[, esc]; keep = ())::AbstractString
escape_string(io, str::AbstractString[, esc]; keep = ())::Nothing
```

对传统 C 和 Unicode 转义序列的一般转义。第一种形式返回转义后的字符串，第二种形式将结果打印到 `io`。

反斜杠 (`\`) 被转义为双反斜杠 (`"\\"`)。不可打印字符要么用其标准 C 转义码转义，NUL 用 `"\0"`（如果不模糊），unicode 代码点（`"\u"` 前缀）或十六进制（`"\x"` 前缀）转义。

可选的 `esc` 参数指定任何其他也应通过前置反斜杠转义的字符（在第一种形式中，`"` 也默认被转义）。

参数 `keep` 指定要保持原样的字符集合。请注意，`esc` 在这里具有优先权。

另请参见 [`unescape_string`](@ref) 以进行反向操作。

!!! compat "Julia 1.7"
    `keep` 参数自 Julia 1.7 起可用。


# 示例

```jldoctest
julia> escape_string("aaa\nbbb")
"aaa\\nbbb"

julia> escape_string("aaa\nbbb"; keep = '\n')
"aaa\nbbb"

julia> escape_string("\xfe\xff") # 无效的 utf-8
"\\xfe\\xff"

julia> escape_string(string('\u2135','\0')) # 不模糊
"ℵ\\0"

julia> escape_string(string('\u2135','\0','0')) # \0 会模糊
"ℵ\\x000"
```
