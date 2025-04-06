```
@uint128_str str
```

将 `str` 解析为 [`UInt128`](@ref)。如果字符串不是有效的整数，则抛出 `ArgumentError`。

# 示例

```
julia> uint128"123456789123"
0x00000000000000000000001cbe991a83

julia> uint128"-123456789123"
错误：LoadError: ArgumentError: 在 "-123456789123" 中的无效基数 10 数字 '-'
[...]
```
