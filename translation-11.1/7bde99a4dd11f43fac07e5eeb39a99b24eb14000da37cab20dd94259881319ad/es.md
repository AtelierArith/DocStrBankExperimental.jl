```
ceil(dt::TimeType, p::Period) -> TimeType
```

Devuelve la `Date` o `DateTime` más cercana mayor o igual a `dt` con resolución `p`.

Para conveniencia, `p` puede ser un tipo en lugar de un valor: `ceil(dt, Dates.Hour)` es un atajo para `ceil(dt, Dates.Hour(1))`.

```jldoctest
julia> ceil(Date(1985, 8, 16), Month)
1985-09-01

julia> ceil(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:45:00

julia> ceil(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```
