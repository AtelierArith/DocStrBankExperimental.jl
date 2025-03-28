```
lastdayofyear(dt::TimeType) -> TimeType
```

Ajuste `dt` au dernier jour de son année.

# Exemples

```jldoctest
julia> lastdayofyear(DateTime("1996-05-20"))
1996-12-31T00:00:00
```
