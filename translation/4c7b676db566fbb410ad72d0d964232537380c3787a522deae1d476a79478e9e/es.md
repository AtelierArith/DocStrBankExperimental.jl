```
firstdayofmonth(dt::TimeType) -> TimeType
```

Ajusta `dt` al primer día de su mes.

# Ejemplos

```jldoctest
julia> firstdayofmonth(DateTime("1996-05-20"))
1996-05-01T00:00:00
```
