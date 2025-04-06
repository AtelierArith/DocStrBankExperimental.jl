```
daysinmonth(dt::TimeType) -> Int
```

返回 `dt` 所在月份的天数。值将为 28、29、30 或 31。

# 示例

```jldoctest
julia> daysinmonth(Date("2000-01"))
31

julia> daysinmonth(Date("2001-02"))
28

julia> daysinmonth(Date("2000-02"))
29
```
