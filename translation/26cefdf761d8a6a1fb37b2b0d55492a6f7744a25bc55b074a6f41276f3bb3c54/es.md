```
lastdayofyear(dt::TimeType) -> TimeType
```

Ajusta `dt` al último día de su año.

# Ejemplos

```jldoctest
julia> lastdayofyear(DateTime("1996-05-20"))
1996-12-31T00:00:00
```
