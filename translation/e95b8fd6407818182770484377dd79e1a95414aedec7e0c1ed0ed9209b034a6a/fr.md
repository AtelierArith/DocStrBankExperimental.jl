```
eps(::Type{DateTime}) -> Milliseconde
eps(::Type{Date}) -> Jour
eps(::Type{Time}) -> Nanoseconde
eps(::TimeType) -> Période
```

Retourne la plus petite valeur d'unité supportée par le `TimeType`.

# Exemples

```jldoctest
julia> eps(DateTime)
1 milliseconde

julia> eps(Date)
1 jour

julia> eps(Time)
1 nanoseconde
```
