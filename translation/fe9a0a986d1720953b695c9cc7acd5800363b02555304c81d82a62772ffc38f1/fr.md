```
dayabbr(dt::TimeType; locale="français") -> String
dayabbr(day::Integer; locale="français") -> String
```

Retourne le nom abrégé correspondant au jour de la semaine de la `Date` ou `DateTime` dans la `locale` donnée. Accepte également un `Integer`.

# Exemples

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"Sam"

julia> dayabbr(3)
"Mer"
```
