```
lastdayofmonth(dt::TimeType) -> TimeType
```

Passt `dt` auf den letzten Tag seines Monats an.

# Beispiele

```jldoctest
julia> lastdayofmonth(DateTime("1996-05-20"))
1996-05-31T00:00:00
```
