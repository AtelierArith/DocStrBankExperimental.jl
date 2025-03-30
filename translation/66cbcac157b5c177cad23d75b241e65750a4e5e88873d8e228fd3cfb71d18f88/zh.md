```
round(x::Period, precision::T, [r::RoundingMode]) where T <: Union{TimePeriod, Week, Day} -> T
```

将 `x` 四舍五入到最接近的 `precision` 的倍数。如果 `x` 和 `precision` 是不同的 `Period` 子类型，则返回值将具有与 `precision` 相同的类型。默认情况下（`RoundNearestTiesUp`），平局（例如，将 90 分钟四舍五入到最接近的小时）将向上舍入。

为了方便，`precision` 可以是类型而不是值：`round(x, Dates.Hour)` 是 `round(x, Dates.Hour(1))` 的快捷方式。

```jldoctest
julia> round(Day(16), Week)
2 weeks

julia> round(Minute(44), Minute(15))
45 minutes

julia> round(Hour(36), Day)
2 days
```

有效的舍入模式 `round(::Period, ::T, ::RoundingMode)` 为 `RoundNearestTiesUp`（默认），`RoundDown`（`floor`），和 `RoundUp`（`ceil`）。

不支持将舍入精度设置为 `Month` 或 `Year`，因为这些 `Period` 的长度不一致。
