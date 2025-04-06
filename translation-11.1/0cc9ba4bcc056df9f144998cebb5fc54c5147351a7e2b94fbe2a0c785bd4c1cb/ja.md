```
monthname(dt::TimeType; locale="日本語") -> String
monthname(month::Integer, locale="日本語") -> String
```

指定された`locale`で`Date`または`DateTime`または`Integer`の月のフルネームを返します。

# 例

```jldoctest
julia> monthname(Date("2005-01-04"))
"1月"

julia> monthname(2)
"2月"
```
