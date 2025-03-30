```
eps(::Type{DateTime}) -> 毫秒
eps(::Type{Date}) -> 天
eps(::Type{Time}) -> 纳秒
eps(::TimeType) -> 周期
```

返回 `TimeType` 支持的最小单位值。

# 示例

```jldoctest
julia> eps(DateTime)
1 毫秒

julia> eps(Date)
1 天

julia> eps(Time)
1 纳秒
```
