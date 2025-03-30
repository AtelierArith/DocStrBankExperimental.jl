```
ceil(dt::TimeType, p::Period) -> TimeType
```

返回大于或等于 `dt` 的最近 `Date` 或 `DateTime`，分辨率为 `p`。

为了方便，`p` 可以是类型而不是值：`ceil(dt, Dates.Hour)` 是 `ceil(dt, Dates.Hour(1))` 的快捷方式。

```jldoctest
julia> ceil(Date(1985, 8, 16), Month)
1985-09-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:45:00

julia> ceil(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```
