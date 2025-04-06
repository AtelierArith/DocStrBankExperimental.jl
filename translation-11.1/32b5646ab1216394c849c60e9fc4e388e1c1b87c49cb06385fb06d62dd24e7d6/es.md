```
daysinyear(dt::TimeType) -> Int
```

Devuelve 366 si el año de `dt` es un año bisiesto, de lo contrario devuelve 365.

# Ejemplos

```jldoctest
julia> daysinyear(1999)
365

julia> daysinyear(2000)
366
```
