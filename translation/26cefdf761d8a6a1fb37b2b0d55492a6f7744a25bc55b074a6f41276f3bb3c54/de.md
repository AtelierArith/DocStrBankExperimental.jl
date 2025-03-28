```
lastdayofyear(dt::TimeType) -> TimeType
```

Passt `dt` auf den letzten Tag seines Jahres an.

# Beispiele

```jldoctest
julia> lastdayofyear(DateTime("1996-05-20"))
1996-12-31T00:00:00
```
