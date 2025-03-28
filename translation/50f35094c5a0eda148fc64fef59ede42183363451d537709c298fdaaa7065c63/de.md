```
canonicalize(::CompoundPeriod) -> CompoundPeriod
```

Reduziert die `CompoundPeriod` in ihre kanonische Form, indem die folgenden Regeln angewendet werden:

  * Jede `Period`, die groß genug ist, um teilweise durch eine gröbere `Period` dargestellt zu werden, wird in mehrere `Period`s zerlegt (z. B. wird `Hour(30)` zu `Day(1) + Hour(6)`)
  * `Period`s mit entgegengesetzten Vorzeichen werden, wenn möglich, kombiniert (z. B. wird `Hour(1) - Day(1)` zu `-Hour(23)`)

# Beispiele

```jldoctest
julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13)))
1 Tag, 1 Stunde

julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1)))
-59 Minuten

julia> canonicalize(Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2)))
1 Monat, -2 Wochen

julia> canonicalize(Dates.CompoundPeriod(Dates.Minute(50000)))
4 Wochen, 6 Tage, 17 Stunden, 20 Minuten
```
