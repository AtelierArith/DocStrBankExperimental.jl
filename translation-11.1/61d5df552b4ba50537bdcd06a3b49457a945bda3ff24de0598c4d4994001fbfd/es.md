```
dayname(dt::TimeType; locale="español") -> String
dayname(day::Integer; locale="español") -> String
```

Devuelve el nombre completo del día correspondiente al día de la semana de la `Fecha` o `FechaHora` en el `locale` dado. También acepta `Integer`.

# Ejemplos

```jldoctest
julia> dayname(Date("2000-01-01"))
"Sábado"

julia> dayname(4)
"Jueves"
```
