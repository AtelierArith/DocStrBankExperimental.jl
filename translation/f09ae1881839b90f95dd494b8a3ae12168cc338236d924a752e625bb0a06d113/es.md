```
floor(dt::TimeType, p::Period) -> TimeType
```

Devuelve la fecha `Date` o `DateTime` más cercana menor o igual a `dt` con resolución `p`.

Para conveniencia, `p` puede ser un tipo en lugar de un valor: `floor(dt, Dates.Hour)` es un atajo para `floor(dt, Dates.Hour(1))`.

```jldoctest
julia> floor(Date(1985, 8, 16), Month)
1985-08-01

julia> floor(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> floor(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-06T00:00:00
```
