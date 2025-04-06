```
struct SimpleColor
```

颜色的基本表示，旨在用于字符串样式。它可以包含一个命名颜色（如 `:red`），或一个 `RGBTuple`，这是一个指定 `r`、`g`、`b` 颜色的 NamedTuple，位深为 8。

# 构造函数

```julia
SimpleColor(name::Symbol)  # 例如 :red
SimpleColor(rgb::RGBTuple) # 例如 (r=1, b=2, g=3)
SimpleColor(r::Integer, b::Integer, b::Integer)
SimpleColor(rgb::UInt32)   # 例如 0x123456
```

另见 `tryparse(SimpleColor, rgb::String)`。
