```
isleapyear(dt::TimeType) -> Bool
```

如果 `dt` 的年份是闰年，则返回 `true`。

# 示例

```jldoctest
julia> isleapyear(Date("2004"))
true

julia> isleapyear(Date("2005"))
false
```
