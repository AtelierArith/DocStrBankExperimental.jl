```
firstdayofweek(dt::TimeType) -> TimeType
```

Passt `dt` auf den Montag seiner Woche an.

# Beispiele

```jldoctest
julia> firstdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-01T00:00:00
```
