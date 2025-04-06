```
dayofweekofmonth(dt::TimeType) -> Int
```

对于 `dt` 的星期几，返回它在 `dt` 所在月份中的编号。因此，如果 `dt` 的星期几是星期一，那么 `1 = 本月的第一个星期一，2 = 本月的第二个星期一，依此类推。` 范围为 1:5。

# 示例

```jldoctest
julia> dayofweekofmonth(Date("2000-02-01"))
1

julia> dayofweekofmonth(Date("2000-02-08"))
2

julia> dayofweekofmonth(Date("2000-02-15"))
3
```
