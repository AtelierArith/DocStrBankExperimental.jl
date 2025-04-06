```
dayofweek(dt::TimeType) -> Int64
```

Devuelve el día de la semana como un [`Int64`](@ref) con `1 = Lunes, 2 = Martes, etc.`.

# Ejemplos

```jldoctest
julia> dayofweek(Date("2000-01-01"))
6
```
