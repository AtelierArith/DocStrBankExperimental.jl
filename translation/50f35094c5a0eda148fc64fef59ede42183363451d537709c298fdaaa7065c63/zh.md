```
canonicalize(::CompoundPeriod) -> CompoundPeriod
```

通过应用以下规则将 `CompoundPeriod` 简化为其规范形式：

  * 任何足够大的 `Period` 将被分解为多个 `Period`（例如，`Hour(30)` 变为 `Day(1) + Hour(6)`）
  * 具有相反符号的 `Period` 将在可能的情况下合并（例如，`Hour(1) - Day(1)` 变为 `-Hour(23)`）

# 示例

```jldoctest
julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13)))
1 day, 1 hour

julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1)))
-59 minutes

julia> canonicalize(Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2)))
1 month, -2 weeks

julia> canonicalize(Dates.CompoundPeriod(Dates.Minute(50000)))
4 weeks, 6 days, 17 hours, 20 minutes
```
