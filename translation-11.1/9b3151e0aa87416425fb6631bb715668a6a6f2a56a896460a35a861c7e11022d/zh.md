```
trunc(dt::TimeType, ::Type{Period}) -> TimeType
```

根据提供的 `Period` 类型截断 `dt` 的值。

# 示例

```jldoctest
julia> trunc(DateTime("1996-01-01T12:30:00"), Day)
1996-01-01T00:00:00
```
