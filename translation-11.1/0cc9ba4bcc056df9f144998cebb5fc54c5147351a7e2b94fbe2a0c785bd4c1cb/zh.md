```
monthname(dt::TimeType; locale="中文") -> String
monthname(month::Integer, locale="中文") -> String
```

返回给定 `locale` 中 `Date` 或 `DateTime` 或 `Integer` 的月份全名。

# 示例

```jldoctest
julia> monthname(Date("2005-01-04"))
"一月"

julia> monthname(2)
"二月"
```
