```
ascii(s::AbstractString)
```

将字符串转换为 `String` 类型，并检查它是否仅包含 ASCII 数据，否则抛出 `ArgumentError`，指示第一个非 ASCII 字节的位置。

另请参见 [`isascii`](@ref) 谓词以过滤或替换非 ASCII 字符。

# 示例

```jldoctest
julia> ascii("abcdeγfgh")
ERROR: ArgumentError: invalid ASCII at index 6 in "abcdeγfgh"
Stacktrace:
[...]

julia> ascii("abcdefgh")
"abcdefgh"
```
