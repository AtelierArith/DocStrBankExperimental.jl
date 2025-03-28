```
dayname(dt::TimeType; locale="français") -> String
dayname(day::Integer; locale="français") -> String
```

Retourne le nom complet du jour correspondant au jour de la semaine de la `Date` ou `DateTime` dans la `locale` donnée. Accepte également un `Integer`.

# Exemples

```jldoctest
julia> dayname(Date("2000-01-01"))
"Samedi"

julia> dayname(4)
"Jeudi"
```
