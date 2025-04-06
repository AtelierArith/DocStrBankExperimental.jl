```
firstdayofweek(dt::TimeType) -> TimeType
```

将 `dt` 调整为其所在周的星期一。

# 示例

```jldoctest
julia> firstdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-01T00:00:00
```
