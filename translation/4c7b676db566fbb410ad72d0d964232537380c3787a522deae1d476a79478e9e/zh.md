```
firstdayofmonth(dt::TimeType) -> TimeType
```

将 `dt` 调整为其月份的第一天。

# 示例

```jldoctest
julia> firstdayofmonth(DateTime("1996-05-20"))
1996-05-01T00:00:00
```
