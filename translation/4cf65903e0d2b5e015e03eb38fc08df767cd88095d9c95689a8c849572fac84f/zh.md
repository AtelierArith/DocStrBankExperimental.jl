```
Dates.ISODateTimeFormat
```

描述了日期和时间的 ISO8601 格式。这是 `DateTime` 的 `Dates.format` 的默认值。

# 示例

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), ISODateTimeFormat)
"2018-08-08T12:00:43.001"
```
