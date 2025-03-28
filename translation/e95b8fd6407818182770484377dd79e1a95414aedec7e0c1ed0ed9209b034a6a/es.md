```
eps(::Type{DateTime}) -> Milisegundo
eps(::Type{Date}) -> Día
eps(::Type{Time}) -> Nanosegundo
eps(::TimeType) -> Período
```

Devuelve el valor de unidad más pequeño soportado por el `TimeType`.

# Ejemplos

```jldoctest
julia> eps(DateTime)
1 milisegundo

julia> eps(Date)
1 día

julia> eps(Time)
1 nanosegundo
```
