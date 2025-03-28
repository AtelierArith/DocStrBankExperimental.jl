```
dayabbr(dt::TimeType; locale="español") -> String
dayabbr(day::Integer; locale="español") -> String
```

Devuelve el nombre abreviado correspondiente al día de la semana de la `Fecha` o `FechaHora` en el `locale` dado. También acepta `Integer`.

# Ejemplos

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"Sab"

julia> dayabbr(3)
"Mié"
```
