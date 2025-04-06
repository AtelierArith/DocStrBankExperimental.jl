```
firstdayofquarter(dt::TimeType) -> TimeType
```

Ajuste `dt` au premier jour de son trimestre.

# Exemples

```jldoctest
julia> firstdayofquarter(DateTime("1996-05-20"))
1996-04-01T00:00:00

julia> firstdayofquarter(DateTime("1996-08-20"))
1996-07-01T00:00:00
```
