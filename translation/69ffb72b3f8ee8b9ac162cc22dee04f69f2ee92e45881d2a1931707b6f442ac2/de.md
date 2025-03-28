```
dayofweek(dt::TimeType) -> Int64
```

Gibt den Wochentag als [`Int64`](@ref) zurück, wobei `1 = Montag, 2 = Dienstag, usw.`.

# Beispiele

```jldoctest
julia> dayofweek(Date("2000-01-01"))
6
```
