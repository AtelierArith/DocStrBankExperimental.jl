```
lastdayofweek(dt::TimeType) -> TimeType
```

Ajusta `dt` al domingo de su semana.

# Ejemplos

```jldoctest
julia> lastdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-07T00:00:00
```
