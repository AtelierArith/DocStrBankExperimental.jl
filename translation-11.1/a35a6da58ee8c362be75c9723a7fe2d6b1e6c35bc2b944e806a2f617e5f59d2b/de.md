```
monthabbr(dt::TimeType; locale="deutsch") -> String
monthabbr(month::Integer, locale="deutsch") -> String
```

Gibt den abgekürzten Monatsnamen des `Date` oder `DateTime` oder `Integer` im angegebenen `locale` zurück.

# Beispiele

```jldoctest
julia> monthabbr(Date("2005-01-04"))
"Jan"

julia> monthabbr(2)
"Feb"
```
