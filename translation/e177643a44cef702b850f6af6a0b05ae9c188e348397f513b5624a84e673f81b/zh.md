```
ceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

将 `x` 向上舍入到最接近的 `precision` 的倍数。如果 `x` 和 `precision` 是不同的 `Period` 子类型，则返回值将具有与 `precision` 相同的类型。

为了方便，`precision` 可以是类型而不是值：`ceil(x, Dates.Hour)` 是 `ceil(x, Dates.Hour(1))` 的快捷方式。

```jldoctest
julia> ceil(Day(16), Week)
3 weeks

julia> ceil(Minute(44), Minute(15))
45 minutes

julia> ceil(Hour(36), Day)
2 days
```

不支持将舍入精度设置为 `Month` 或 `Year`，因为这些 `Period` 的长度不一致。
