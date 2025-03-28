```
firstdayofyear(dt::TimeType) -> TimeType
```

Passt `dt` auf den ersten Tag seines Jahres an.

# Beispiele

```jldoctest
julia> firstdayofyear(DateTime("1996-05-20"))
1996-01-01T00:00:00
```
