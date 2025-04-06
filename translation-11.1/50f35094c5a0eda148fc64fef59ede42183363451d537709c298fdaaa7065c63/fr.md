```
canonicalize(::CompoundPeriod) -> CompoundPeriod
```

Réduit le `CompoundPeriod` à sa forme canonique en appliquant les règles suivantes :

  * Tout `Period` suffisamment grand pour être partiellement représentable par un `Period` plus grossier sera divisé en plusieurs `Period`s (par exemple, `Hour(30)` devient `Day(1) + Hour(6)`)
  * Les `Period`s avec des signes opposés seront combinés lorsque cela est possible (par exemple, `Hour(1) - Day(1)` devient `-Hour(23)`)

# Exemples

```jldoctest
julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13)))
1 jour, 1 heure

julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1)))
-59 minutes

julia> canonicalize(Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2)))
1 mois, -2 semaines

julia> canonicalize(Dates.CompoundPeriod(Dates.Minute(50000)))
4 semaines, 6 jours, 17 heures, 20 minutes
```
