```
dayname(dt::TimeType; locale="japanese") -> String
dayname(day::Integer; locale="japanese") -> String
```

与えられた `locale` における `Date` または `DateTime` の曜日に対応する完全な曜日名を返します。整数も受け付けます。

# 例

```jldoctest
julia> dayname(Date("2000-01-01"))
"土曜日"

julia> dayname(4)
"木曜日"
```
