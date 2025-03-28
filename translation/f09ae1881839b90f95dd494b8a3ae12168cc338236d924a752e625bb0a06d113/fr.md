```
floor(dt::TimeType, p::Period) -> TimeType
```

Renvoie la date ou la date-heure la plus proche inférieure ou égale à `dt` à la résolution `p`.

Pour plus de commodité, `p` peut être un type au lieu d'une valeur : `floor(dt, Dates.Hour)` est un raccourci pour `floor(dt, Dates.Hour(1))`.

```jldoctest
julia> floor(Date(1985, 8, 16), Month)
1985-08-01

julia> floor(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> floor(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-06T00:00:00
```
