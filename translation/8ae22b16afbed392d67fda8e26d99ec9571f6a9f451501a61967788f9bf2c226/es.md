```
daysofweekinmonth(dt::TimeType) -> Int
```

Para el día de la semana de `dt`, devuelve el número total de ese día de la semana en el mes de `dt`. Devuelve 4 o 5. Útil en expresiones temporales para especificar el último día de una semana en un mes incluyendo `dayofweekofmonth(dt) == daysofweekinmonth(dt)` en la función ajustadora.

# Ejemplos

```jldoctest
julia> daysofweekinmonth(Date("2005-01-01"))
5

julia> daysofweekinmonth(Date("2005-01-04"))
4
```
