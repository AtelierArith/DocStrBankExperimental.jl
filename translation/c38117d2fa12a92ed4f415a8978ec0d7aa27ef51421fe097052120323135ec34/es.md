```
CompoundPeriod(periods) -> CompoundPeriod
```

Construye un `CompoundPeriod` a partir de un `Vector` de `Period`s. Todos los `Period`s del mismo tipo se sumarán.

# Ejemplos

```jldoctest
julia> Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13))
25 hours

julia> Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1))
-1 hour, 1 minute

julia> Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2))
1 month, -2 weeks

julia> Dates.CompoundPeriod(Dates.Minute(50000))
50000 minutes
```
