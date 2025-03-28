```
week(dt::TimeType) -> Int64
```

Devuelve la [fecha de la semana ISO](https://es.wikipedia.org/wiki/Fecha_de_la_semana_ISO) de un `Date` o `DateTime` como un [`Int64`](@ref). Ten en cuenta que la primera semana de un año es la semana que contiene el primer jueves del año, lo que puede resultar en fechas anteriores al 4 de enero que estén en la última semana del año anterior. Por ejemplo, `week(Date(2005, 1, 1))` es la 53ª semana de 2004.

# Ejemplos

```jldoctest
julia> week(Date(1989, 6, 22))
25

julia> week(Date(2005, 1, 1))
53

julia> week(Date(2004, 12, 31))
53
```
