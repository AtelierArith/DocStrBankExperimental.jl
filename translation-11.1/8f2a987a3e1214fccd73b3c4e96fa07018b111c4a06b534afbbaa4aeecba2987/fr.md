```
lastdayofweek(dt::TimeType) -> TimeType
```

Ajuste `dt` au dimanche de sa semaine.

# Exemples

```jldoctest
julia> lastdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-07T00:00:00
```
