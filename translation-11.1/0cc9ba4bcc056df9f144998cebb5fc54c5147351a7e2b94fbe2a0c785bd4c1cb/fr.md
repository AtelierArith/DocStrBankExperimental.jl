```
monthname(dt::TimeType; locale="français") -> String
monthname(month::Integer, locale="français") -> String
```

Retourne le nom complet du mois de la `Date` ou `DateTime` ou `Integer` dans la `locale` donnée.

# Exemples

```jldoctest
julia> monthname(Date("2005-01-04"))
"Janvier"

julia> monthname(2)
"Février"
```
