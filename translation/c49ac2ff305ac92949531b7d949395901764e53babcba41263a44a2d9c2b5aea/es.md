```
floor(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

Redondea `x` hacia abajo al múltiplo más cercano de `precision`. Si `x` y `precision` son diferentes subtipos de `Period`, el valor de retorno tendrá el mismo tipo que `precision`.

Para conveniencia, `precision` puede ser un tipo en lugar de un valor: `floor(x, Dates.Hour)` es un atajo para `floor(x, Dates.Hour(1))`.

```jldoctest
julia> floor(Day(16), Week)
2 weeks

julia> floor(Minute(44), Minute(15))
30 minutes

julia> floor(Hour(36), Day)
1 day
```

No se admite el redondeo a una `precision` de `Month`s o `Year`s, ya que estos `Period`s tienen una longitud inconsistente. ```
