```
lastdayofyear(dt::TimeType) -> TimeType
```

将 `dt` 调整为其年份的最后一天。

# 示例

```jldoctest
julia> lastdayofyear(DateTime("1996-05-20"))
1996-12-31T00:00:00
```
