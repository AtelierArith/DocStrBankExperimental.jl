```
lastdayofmonth(dt::TimeType) -> TimeType
```

将 `dt` 调整为其月份的最后一天。

# 示例

```jldoctest
julia> lastdayofmonth(DateTime("1996-05-20"))
1996-05-31T00:00:00
```
