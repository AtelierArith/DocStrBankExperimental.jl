```
dayofweek(dt::TimeType) -> Int64
```

Renvoie le jour de la semaine sous forme d'un [`Int64`](@ref) avec `1 = Lundi, 2 = Mardi, etc.`.

# Exemples

```jldoctest
julia> dayofweek(Date("2000-01-01"))
6
```
