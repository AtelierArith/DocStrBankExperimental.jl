```
lastdayofweek(dt::TimeType) -> TimeType
```

将 `dt` 调整为其所在周的星期日。

# 示例

```jldoctest
julia> lastdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-07T00:00:00
```
