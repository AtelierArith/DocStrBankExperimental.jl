```
dayname(dt::TimeType; locale="deutsch") -> String
dayname(day::Integer; locale="deutsch") -> String
```

Gibt den vollständigen Namen des Wochentags entsprechend dem Wochentag des `Date` oder `DateTime` im angegebenen `locale` zurück. Akzeptiert auch `Integer`.

# Beispiele

```jldoctest
julia> dayname(Date("2000-01-01"))
"Samstag"

julia> dayname(4)
"Donnerstag"
```
