```
@int128_str str
```

将 `str` 解析为 [`Int128`](@ref)。如果字符串不是有效的整数，则抛出 `ArgumentError`。

# 示例

```jldoctest
julia> int128"123456789123"
123456789123

julia> int128"123456789123.4"
ERROR: LoadError: ArgumentError: invalid base 10 digit '.' in "123456789123.4"
[...]
```
