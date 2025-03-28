```
daysinyear(dt::TimeType) -> Int
```

Gibt 366 zurück, wenn das Jahr von `dt` ein Schaltjahr ist, andernfalls gibt es 365 zurück.

# Beispiele

```jldoctest
julia> daysinyear(1999)
365

julia> daysinyear(2000)
366
```
