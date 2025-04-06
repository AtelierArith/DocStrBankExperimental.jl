```
canonicalize(::CompoundPeriod) -> CompoundPeriod
```

Reduce el `CompoundPeriod` a su forma canónica aplicando las siguientes reglas:

  * Cualquier `Period` lo suficientemente grande como para ser representado parcialmente por un `Period` más grueso se descompondrá en múltiples `Period`s (por ejemplo, `Hour(30)` se convierte en `Day(1) + Hour(6)`)
  * Los `Period`s con signos opuestos se combinarán cuando sea posible (por ejemplo, `Hour(1) - Day(1)` se convierte en `-Hour(23)`)

# Ejemplos

```jldoctest
julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13)))
1 día, 1 hora

julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1)))
-59 minutos

julia> canonicalize(Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2)))
1 mes, -2 semanas

julia> canonicalize(Dates.CompoundPeriod(Dates.Minute(50000)))
4 semanas, 6 días, 17 horas, 20 minutos
```
