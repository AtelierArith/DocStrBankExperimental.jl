```
monthabbr(dt::TimeType; locale="日本語") -> String
monthabbr(month::Integer, locale="日本語") -> String
```

指定された`locale`での`Date`または`DateTime`または`Integer`の省略形の月名を返します。

# 例

```jldoctest
julia> monthabbr(Date("2005-01-04"))
"1月"

julia> monthabbr(2)
"2月"
```
