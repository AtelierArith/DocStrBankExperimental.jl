```
firstdayofquarter(dt::TimeType) -> TimeType
```

将 `dt` 调整为其季度的第一天。

# 示例

```jldoctest
julia> firstdayofquarter(DateTime("1996-05-20"))
1996-04-01T00:00:00

julia> firstdayofquarter(DateTime("1996-08-20"))
1996-07-01T00:00:00
```
