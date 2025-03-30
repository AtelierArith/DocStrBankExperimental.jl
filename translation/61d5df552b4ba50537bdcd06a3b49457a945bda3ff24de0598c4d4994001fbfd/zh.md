```
dayname(dt::TimeType; locale="中文") -> String
dayname(day::Integer; locale="中文") -> String
```

返回与给定 `Date` 或 `DateTime` 的星期几对应的完整星期名称，使用指定的 `locale`。也接受 `Integer`。

# 示例

```jldoctest
julia> dayname(Date("2000-01-01"))
"星期六"

julia> dayname(4)
"星期四"
```
