```
firstdayofmonth(dt::TimeType) -> TimeType
```

Passt `dt` auf den ersten Tag seines Monats an.

# Beispiele

```jldoctest
julia> firstdayofmonth(DateTime("1996-05-20"))
1996-05-01T00:00:00
```
