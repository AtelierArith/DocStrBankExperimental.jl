```
daysinmonth(dt::TimeType) -> Int
```

Retourne le nombre de jours dans le mois de `dt`. La valeur sera 28, 29, 30 ou 31.

# Exemples

```jldoctest
julia> daysinmonth(Date("2000-01"))
31

julia> daysinmonth(Date("2001-02"))
28

julia> daysinmonth(Date("2000-02"))
29
```
