```
daysofweekinmonth(dt::TimeType) -> Int
```

对于 `dt` 的星期几，返回 `dt` 所在月份中该星期几的总数。返回值为 4 或 5。在时间表达式中很有用，可以通过在调整函数中包含 `dayofweekofmonth(dt) == daysofweekinmonth(dt)` 来指定一个月份中最后一天的星期几。

# 示例

```jldoctest
julia> daysofweekinmonth(Date("2005-01-01"))
5

julia> daysofweekinmonth(Date("2005-01-04"))
4
```
