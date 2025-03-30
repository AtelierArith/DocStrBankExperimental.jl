```
floor(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

将 `x` 向下舍入到最接近的 `precision` 的倍数。如果 `x` 和 `precision` 是不同的 `Period` 子类型，则返回值将具有与 `precision` 相同的类型。

为了方便，`precision` 可以是类型而不是值：`floor(x, Dates.Hour)` 是 `floor(x, Dates.Hour(1))` 的快捷方式。

```jldoctest
julia> floor(Day(16), Week)
2 weeks

julia> floor(Minute(44), Minute(15))
30 minutes

julia> floor(Hour(36), Day)
1 day
```

不支持舍入到 `Month` 或 `Year` 的 `precision`，因为这些 `Period` 的长度不一致。
