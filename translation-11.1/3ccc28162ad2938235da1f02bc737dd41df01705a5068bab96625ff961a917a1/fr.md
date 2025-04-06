```
firstdayofyear(dt::TimeType) -> TimeType
```

Ajuste `dt` au premier jour de son année.

# Exemples

```jldoctest
julia> firstdayofyear(DateTime("1996-05-20"))
1996-01-01T00:00:00
```
