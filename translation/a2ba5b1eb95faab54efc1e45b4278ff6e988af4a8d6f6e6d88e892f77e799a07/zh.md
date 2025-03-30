```
now(::Type{UTC}) -> DateTime
```

返回一个与用户系统时间相对应的 `DateTime`，以 UTC/GMT 表示。有关其他时区的信息，请参见 TimeZones.jl 包。

# 示例

```julia
julia> now(UTC)
2023-01-04T10:52:24.864
```
