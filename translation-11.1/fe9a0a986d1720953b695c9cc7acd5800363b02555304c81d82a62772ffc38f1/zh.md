```
dayabbr(dt::TimeType; locale="中文") -> String
dayabbr(day::Integer; locale="中文") -> String
```

返回与给定 `Date` 或 `DateTime` 的星期几对应的缩写名称，使用指定的 `locale`。也接受 `Integer`。

# 示例

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"Sat"

julia> dayabbr(3)
"Wed"
```
