```
monthabbr(dt::TimeType; locale="español") -> String
monthabbr(month::Integer, locale="español") -> String
```

Devuelve el nombre abreviado del mes del `Date` o `DateTime` o `Integer` en el `locale` dado.

# Ejemplos

```jldoctest
julia> monthabbr(Date("2005-01-04"))
"Ene"

julia> monthabbr(2)
"Feb"
```
