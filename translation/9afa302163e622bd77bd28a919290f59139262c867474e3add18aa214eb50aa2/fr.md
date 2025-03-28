```
round(dt::TimeType, p::Period, [r::RoundingMode]) -> TimeType
```

Renvoie la `Date` ou `DateTime` la plus proche de `dt` à la résolution `p`. Par défaut (`RoundNearestTiesUp`), les égalités (par exemple, arrondir 9:30 à l'heure la plus proche) seront arrondies vers le haut.

Pour plus de commodité, `p` peut être un type au lieu d'une valeur : `round(dt, Dates.Hour)` est un raccourci pour `round(dt, Dates.Hour(1))`.

```jldoctest
julia> round(Date(1985, 8, 16), Month)
1985-08-01

julia> round(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> round(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```

Les modes d'arrondi valides pour `round(::TimeType, ::Period, ::RoundingMode)` sont `RoundNearestTiesUp` (par défaut), `RoundDown` (`floor`), et `RoundUp` (`ceil`).
