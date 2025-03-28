```
dayofweekofmonth(dt::TimeType) -> Int
```

Pour le jour de la semaine de `dt`, renvoie quel numéro il est dans le mois de `dt`. Donc, si le jour de la semaine de `dt` est lundi, alors `1 = Premier lundi du mois, 2 = Deuxième lundi du mois, etc.` Dans la plage 1:5.

# Exemples

```jldoctest
julia> dayofweekofmonth(Date("2000-02-01"))
1

julia> dayofweekofmonth(Date("2000-02-08"))
2

julia> dayofweekofmonth(Date("2000-02-15"))
3
```
