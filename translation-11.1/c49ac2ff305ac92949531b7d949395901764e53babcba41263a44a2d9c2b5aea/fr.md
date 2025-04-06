```
floor(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

Arrondir `x` vers le bas au multiple le plus proche de `precision`. Si `x` et `precision` sont des sous-types différents de `Period`, la valeur de retour aura le même type que `precision`.

Pour plus de commodité, `precision` peut être un type au lieu d'une valeur : `floor(x, Dates.Hour)` est un raccourci pour `floor(x, Dates.Hour(1))`.

```jldoctest
julia> floor(Day(16), Week)
2 semaines

julia> floor(Minute(44), Minute(15))
30 minutes

julia> floor(Hour(36), Day)
1 jour
```

L'arrondi à une `precision` de `Month`s ou `Year`s n'est pas supporté, car ces `Period`s ont une longueur incohérente. ```
