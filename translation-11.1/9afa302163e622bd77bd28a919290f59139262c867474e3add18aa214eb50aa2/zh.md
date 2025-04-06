```
round(dt::TimeType, p::Period, [r::RoundingMode]) -> TimeType
```

返回与 `dt` 最近的 `Date` 或 `DateTime`，分辨率为 `p`。默认情况下（`RoundNearestTiesUp`），平局（例如，将 9:30 四舍五入到最近的小时）将向上舍入。

为了方便，`p` 可以是类型而不是值：`round(dt, Dates.Hour)` 是 `round(dt, Dates.Hour(1))` 的快捷方式。

```jldoctest
julia> round(Date(1985, 8, 16), Month)
1985-08-01

julia> round(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> round(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```

有效的舍入模式为 `round(::TimeType, ::Period, ::RoundingMode)` 的有 `RoundNearestTiesUp`（默认）、`RoundDown`（`floor`）和 `RoundUp`（`ceil`）。
