```
ceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

Redondea `x` hacia arriba al múltiplo más cercano de `precision`. Si `x` y `precision` son diferentes subtipos de `Period`, el valor de retorno tendrá el mismo tipo que `precision`.

Para conveniencia, `precision` puede ser un tipo en lugar de un valor: `ceil(x, Dates.Hour)` es un atajo para `ceil(x, Dates.Hour(1))`.

```jldoctest
julia> ceil(Day(16), Week)
3 weeks

julia> ceil(Minute(44), Minute(15))
45 minutes

julia> ceil(Hour(36), Day)
2 days
```

No se admite el redondeo a una `precision` de `Month`s o `Year`s, ya que estos `Period`s tienen una longitud inconsistente. ```
