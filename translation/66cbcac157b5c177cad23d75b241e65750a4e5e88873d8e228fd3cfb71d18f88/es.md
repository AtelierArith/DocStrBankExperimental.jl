```
round(x::Period, precision::T, [r::RoundingMode]) where T <: Union{TimePeriod, Week, Day} -> T
```

Redondea `x` al múltiplo más cercano de `precision`. Si `x` y `precision` son diferentes subtipos de `Period`, el valor de retorno tendrá el mismo tipo que `precision`. Por defecto (`RoundNearestTiesUp`), los empates (por ejemplo, redondear 90 minutos a la hora más cercana) se redondearán hacia arriba.

Para mayor comodidad, `precision` puede ser un tipo en lugar de un valor: `round(x, Dates.Hour)` es un atajo para `round(x, Dates.Hour(1))`.

```jldoctest
julia> round(Day(16), Week)
2 weeks

julia> round(Minute(44), Minute(15))
45 minutes

julia> round(Hour(36), Day)
2 days
```

Los modos de redondeo válidos para `round(::Period, ::T, ::RoundingMode)` son `RoundNearestTiesUp` (por defecto), `RoundDown` (`floor`), y `RoundUp` (`ceil`).

No se admite el redondeo a una `precision` de `Month`s o `Year`s, ya que estos `Period`s son de longitud inconsistente.
