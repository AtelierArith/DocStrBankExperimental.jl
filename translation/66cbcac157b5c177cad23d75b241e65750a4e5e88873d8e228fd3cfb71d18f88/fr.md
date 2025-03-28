```
round(x::Period, precision::T, [r::RoundingMode]) where T <: Union{TimePeriod, Week, Day} -> T
```

Arrondir `x` au multiple le plus proche de `precision`. Si `x` et `precision` sont des sous-types différents de `Period`, la valeur de retour aura le même type que `precision`. Par défaut (`RoundNearestTiesUp`), les égalités (par exemple, arrondir 90 minutes à l'heure la plus proche) seront arrondies vers le haut.

Pour plus de commodité, `precision` peut être un type au lieu d'une valeur : `round(x, Dates.Hour)` est un raccourci pour `round(x, Dates.Hour(1))`.

```jldoctest
julia> round(Day(16), Week)
2 weeks

julia> round(Minute(44), Minute(15))
45 minutes

julia> round(Hour(36), Day)
2 days
```

Les modes d'arrondi valides pour `round(::Period, ::T, ::RoundingMode)` sont `RoundNearestTiesUp` (par défaut), `RoundDown` (`floor`), et `RoundUp` (`ceil`).

L'arrondi à une `precision` de `Month`s ou `Year`s n'est pas supporté, car ces `Period`s ont une longueur incohérente.
