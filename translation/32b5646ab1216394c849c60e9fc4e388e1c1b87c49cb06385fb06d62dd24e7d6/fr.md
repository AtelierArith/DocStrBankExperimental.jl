```
daysinyear(dt::TimeType) -> Int
```

Retourne 366 si l'année de `dt` est une année bissextile, sinon retourne 365.

# Exemples

```jldoctest
julia> daysinyear(1999)
365

julia> daysinyear(2000)
366
```
