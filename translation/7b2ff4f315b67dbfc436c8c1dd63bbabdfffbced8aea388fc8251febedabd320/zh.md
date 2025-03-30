```
week(dt::TimeType) -> Int64
```

返回 `Date` 或 `DateTime` 的 [ISO 周日期](https://en.wikipedia.org/wiki/ISO_week_date) 作为 [`Int64`](@ref)。请注意，一年的第一周是包含该年第一周四的那一周，这可能导致在1月4日之前的日期属于前一年的最后一周。例如，`week(Date(2005, 1, 1))` 是2004年的第53周。

# 示例

```jldoctest
julia> week(Date(1989, 6, 22))
25

julia> week(Date(2005, 1, 1))
53

julia> week(Date(2004, 12, 31))
53
```
