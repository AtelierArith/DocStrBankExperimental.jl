```
monthabbr(dt::TimeType; locale="français") -> String
monthabbr(month::Integer, locale="français") -> String
```

Retourne le nom du mois abrégé de la `Date` ou `DateTime` ou `Integer` dans le `locale` donné.

# Exemples

```jldoctest
julia> monthabbr(Date("2005-01-04"))
"Jan"

julia> monthabbr(2)
"Fév"
```
