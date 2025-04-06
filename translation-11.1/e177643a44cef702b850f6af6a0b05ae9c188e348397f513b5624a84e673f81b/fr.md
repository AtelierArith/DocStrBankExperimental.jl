```
ceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

Arrondir `x` à la multiple supérieur le plus proche de `precision`. Si `x` et `precision` sont des sous-types différents de `Period`, la valeur de retour aura le même type que `precision`.

Pour plus de commodité, `precision` peut être un type au lieu d'une valeur : `ceil(x, Dates.Hour)` est un raccourci pour `ceil(x, Dates.Hour(1))`.

```jldoctest
julia> ceil(Day(16), Week)
3 weeks

julia> ceil(Minute(44), Minute(15))
45 minutes

julia> ceil(Hour(36), Day)
2 days
```

L'arrondi à une `precision` de `Month`s ou `Year`s n'est pas supporté, car ces `Period`s ont une longueur incohérente.
