```
dayofweek(dt::TimeType) -> Int64
```

返回一周中的天数，作为一个 [`Int64`](@ref)，其中 `1 = 星期一，2 = 星期二，等等。`

# 示例

```jldoctest
julia> dayofweek(Date("2000-01-01"))
6
```
