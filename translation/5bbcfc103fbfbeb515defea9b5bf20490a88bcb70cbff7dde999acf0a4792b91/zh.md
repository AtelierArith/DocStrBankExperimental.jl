```
lastdayofquarter(dt::TimeType) -> TimeType
```

将 `dt` 调整为其季度的最后一天。

# 示例

```jldoctest
julia> lastdayofquarter(DateTime("1996-05-20"))
1996-06-30T00:00:00

julia> lastdayofquarter(DateTime("1996-08-20"))
1996-09-30T00:00:00
```
