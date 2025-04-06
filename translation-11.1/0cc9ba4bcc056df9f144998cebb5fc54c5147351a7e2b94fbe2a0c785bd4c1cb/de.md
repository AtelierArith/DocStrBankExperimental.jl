```
monthname(dt::TimeType; locale="deutsch") -> String
monthname(month::Integer, locale="deutsch") -> String
```

Gibt den vollständigen Namen des Monats des `Date` oder `DateTime` oder `Integer` im angegebenen `locale` zurück.

# Beispiele

```jldoctest
julia> monthname(Date("2005-01-04"))
"Januar"

julia> monthname(2)
"Februar"
```
