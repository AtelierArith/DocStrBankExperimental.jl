```
dayofweekofmonth(dt::TimeType) -> Int
```

Para el día de la semana de `dt`, devuelve qué número es en el mes de `dt`. Así que si el día de la semana de `dt` es lunes, entonces `1 = Primer lunes del mes, 2 = Segundo lunes del mes, etc.` En el rango 1:5.

# Ejemplos

```jldoctest
julia> dayofweekofmonth(Date("2000-02-01"))
1

julia> dayofweekofmonth(Date("2000-02-08"))
2

julia> dayofweekofmonth(Date("2000-02-15"))
3
```
