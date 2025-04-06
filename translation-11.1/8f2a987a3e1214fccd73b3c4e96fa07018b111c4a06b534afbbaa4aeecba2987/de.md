```
lastdayofweek(dt::TimeType) -> TimeType
```

Passt `dt` auf den Sonntag seiner Woche an.

# Beispiele

```jldoctest
julia> lastdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-07T00:00:00
```
