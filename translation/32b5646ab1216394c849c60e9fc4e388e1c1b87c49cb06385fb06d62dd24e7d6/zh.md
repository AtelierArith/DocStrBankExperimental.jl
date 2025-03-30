```
daysinyear(dt::TimeType) -> Int
```

如果 `dt` 的年份是闰年，则返回 366，否则返回 365。

# 示例

```jldoctest
julia> daysinyear(1999)
365

julia> daysinyear(2000)
366
```
