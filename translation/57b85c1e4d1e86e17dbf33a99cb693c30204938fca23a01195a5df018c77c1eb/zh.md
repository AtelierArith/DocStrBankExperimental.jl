```
escape_raw_string(s::AbstractString, delim='"') -> AbstractString
escape_raw_string(io, s::AbstractString, delim='"')
```

以解析原始字符串字面量的方式转义字符串。对于输入字符串 `s` 中的每个双引号 (`"`) 字符（如果指定了 `delim` 则使用 `delim`），此函数计算前面反斜杠 (`\`) 字符的数量 *n*，然后将反斜杠的数量从 *n* 增加到 2*n*+1（即使 *n* = 0 也如此）。它还会将字符串末尾的反斜杠序列加倍。

这种转义约定用于原始字符串和其他非标准字符串字面量。（它恰好也是 Microsoft C/C++ 编译器运行时在将命令行字符串解析为 argv[] 数组时所期望的转义约定。）

另见 [`escape_string`](@ref).
