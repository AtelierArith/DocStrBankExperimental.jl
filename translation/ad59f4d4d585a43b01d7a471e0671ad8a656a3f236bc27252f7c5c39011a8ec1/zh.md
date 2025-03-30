```
Dates.ISOTimeFormat
```

描述了时间的 ISO8601 格式。这是 `Time` 的 `Dates.format` 的默认值。

# 示例

```jldoctest
julia> Dates.format(Time(12, 0, 43, 1), ISOTimeFormat)
"12:00:43.001"
```
