```
CompoundPeriod(periods) -> CompoundPeriod
```

Konstruiere eine `CompoundPeriod` aus einem `Vector` von `Period`s. Alle `Period`s desselben Typs werden zusammenaddiert.

# Beispiele

```jldoctest
julia> Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13))
25 Stunden

julia> Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1))
-1 Stunde, 1 Minute

julia> Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2))
1 Monat, -2 Wochen

julia> Dates.CompoundPeriod(Dates.Minute(50000))
50000 Minuten
```
