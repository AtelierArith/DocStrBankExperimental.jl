```
dayabbr(dt::TimeType; locale="deutsch") -> String
dayabbr(day::Integer; locale="deutsch") -> String
```

Gibt den abgekürzten Namen des Wochentags des `Date` oder `DateTime` im angegebenen `locale` zurück. Akzeptiert auch `Integer`.

# Beispiele

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"Sa"

julia> dayabbr(3)
"Mi"
```
