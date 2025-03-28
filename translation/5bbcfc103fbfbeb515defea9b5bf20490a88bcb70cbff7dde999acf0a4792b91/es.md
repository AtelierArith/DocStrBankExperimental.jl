```
lastdayofquarter(dt::TimeType) -> TimeType
```

Ajusta `dt` al último día de su trimestre.

# Ejemplos

```jldoctest
julia> lastdayofquarter(DateTime("1996-05-20"))
1996-06-30T00:00:00

julia> lastdayofquarter(DateTime("1996-08-20"))
1996-09-30T00:00:00
```
