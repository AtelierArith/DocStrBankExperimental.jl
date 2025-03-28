```
daysofweekinmonth(dt::TimeType) -> Int
```

Pour le jour de la semaine de `dt`, retourne le nombre total de ce jour de la semaine dans le mois de `dt`. Retourne 4 ou 5. Utile dans les expressions temporelles pour spécifier le dernier jour d'une semaine dans un mois en incluant `dayofweekofmonth(dt) == daysofweekinmonth(dt)` dans la fonction d'ajustement.

# Exemples

```jldoctest
julia> daysofweekinmonth(Date("2005-01-01"))
5

julia> daysofweekinmonth(Date("2005-01-04"))
4
```
