```
lastdayofmonth(dt::TimeType) -> TimeType
```

Ajuste `dt` au dernier jour de son mois.

# Exemples

```jldoctest
julia> lastdayofmonth(DateTime("1996-05-20"))
1996-05-31T00:00:00
```
