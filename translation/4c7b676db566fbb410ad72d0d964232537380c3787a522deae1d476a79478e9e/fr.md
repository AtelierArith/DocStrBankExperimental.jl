```
firstdayofmonth(dt::TimeType) -> TimeType
```

Ajuste `dt` au premier jour de son mois.

# Exemples

```jldoctest
julia> firstdayofmonth(DateTime("1996-05-20"))
1996-05-01T00:00:00
```
