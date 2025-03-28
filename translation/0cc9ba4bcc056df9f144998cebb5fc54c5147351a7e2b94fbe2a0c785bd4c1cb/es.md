```
monthname(dt::TimeType; locale="español") -> String
monthname(month::Integer, locale="español") -> String
```

Devuelve el nombre completo del mes del `Date` o `DateTime` o `Integer` en el `locale` dado.

# Ejemplos

```jldoctest
julia> monthname(Date("2005-01-04"))
"Enero"

julia> monthname(2)
"Febrero"
```
