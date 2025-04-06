```
unescape_string(str::AbstractString, keep = ())::AbstractString
unescape_string(io, s::AbstractString, keep = ())::Nothing
```

对传统 C 和 Unicode 转义序列的一般解码。第一种形式返回解码后的字符串，第二种形式将结果打印到 `io`。参数 `keep` 指定了一组字符（连同反斜杠）应保持原样。

以下转义序列被识别：

  * 转义反斜杠 (`\\`)
  * 转义双引号 (`\"`)
  * 标准 C 转义序列 (`\a`, `\b`, `\t`, `\n`, `\v`, `\f`, `\r`, `\e`)
  * Unicode BMP 码点 (`\u` 后跟 1-4 个十六进制数字)
  * 所有 Unicode 码点 (`\U` 后跟 1-8 个十六进制数字；最大值 = 0010ffff)
  * 十六进制字节 (`\x` 后跟 1-2 个十六进制数字)
  * 八进制字节 (`\` 后跟 1-3 个八进制数字)

另见 [`escape_string`](@ref)。

# 示例

```jldoctest
julia> unescape_string("aaa\\nbbb") # C 转义序列
"aaa\nbbb"

julia> unescape_string("\\u03c0") # unicode
"π"

julia> unescape_string("\\101") # 八进制
"A"

julia> unescape_string("aaa \\g \\n", ['g']) # 使用 `keep` 参数
"aaa \\g \n"
```
