```
strip([pred=isspace,] str::AbstractString) -> SubString
strip(str::AbstractString, chars) -> SubString
```

从 `str` 中移除前导和尾随字符，可以是由 `chars` 指定的字符，或者是 `pred` 函数返回 `true` 的字符。

默认行为是移除前导和尾随的空白和分隔符：有关详细信息，请参见 [`isspace`](@ref)。

可选的 `chars` 参数指定要移除的字符：它可以是单个字符、字符向量或字符集合。

另请参见 [`lstrip`](@ref) 和 [`rstrip`](@ref)。

!!! compat "Julia 1.2"
    接受谓词函数的方法需要 Julia 1.2 或更高版本。


# 示例

```jldoctest
julia> strip("{3, 5}\n", ['{', '}', '\n'])
"3, 5"
```
