```
firstdayofyear(dt::TimeType) -> TimeType
```

将 `dt` 调整为其年份的第一天。

# 示例

```jldoctest
julia> firstdayofyear(DateTime("1996-05-20"))
1996-01-01T00:00:00
```
