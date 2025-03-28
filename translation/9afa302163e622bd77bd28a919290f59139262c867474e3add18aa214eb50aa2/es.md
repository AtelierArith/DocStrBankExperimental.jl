```
round(dt::TimeType, p::Period, [r::RoundingMode]) -> TimeType
```

Devuelve la `Date` o `DateTime` más cercana a `dt` con la resolución `p`. Por defecto (`RoundNearestTiesUp`), los empates (por ejemplo, redondear 9:30 a la hora más cercana) se redondearán hacia arriba.

Para conveniencia, `p` puede ser un tipo en lugar de un valor: `round(dt, Dates.Hour)` es un atajo para `round(dt, Dates.Hour(1))`.

```jldoctest
julia> round(Date(1985, 8, 16), Month)
1985-08-01

julia> round(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> round(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```

Los modos de redondeo válidos para `round(::TimeType, ::Period, ::RoundingMode)` son `RoundNearestTiesUp` (por defecto), `RoundDown` (`floor`), y `RoundUp` (`ceil`).
