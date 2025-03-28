```
CompoundPeriod(periods) -> CompoundPeriod
```

Construit un `CompoundPeriod` à partir d'un `Vector` de `Period`s. Tous les `Period`s du même type seront additionnés.

# Exemples

```jldoctest
julia> Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13))
25 heures

julia> Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1))
-1 heure, 1 minute

julia> Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2))
1 mois, -2 semaines

julia> Dates.CompoundPeriod(Dates.Minute(50000))
50000 minutes
```
