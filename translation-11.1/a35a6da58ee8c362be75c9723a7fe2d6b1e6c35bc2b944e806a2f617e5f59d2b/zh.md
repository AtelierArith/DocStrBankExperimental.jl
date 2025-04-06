```
monthabbr(dt::TimeType; locale="中文") -> String
monthabbr(month::Integer, locale="中文") -> String
```

返回给定 `locale` 的 `Date` 或 `DateTime` 或 `Integer` 的缩写月份名称。

# 示例

```jldoctest
julia> monthabbr(Date("2005-01-04"))
"一月"

julia> monthabbr(2)
"二月"
```
