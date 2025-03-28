```
firstdayofweek(dt::TimeType) -> TimeType
```

Ajusta `dt` al lunes de su semana.

# Ejemplos

```jldoctest
julia> firstdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-01T00:00:00
```
