```
lastdayofmonth(dt::TimeType) -> TimeType
```

Ajusta `dt` al último día de su mes.

# Ejemplos

```jldoctest
julia> lastdayofmonth(DateTime("1996-05-20"))
1996-05-31T00:00:00
```
