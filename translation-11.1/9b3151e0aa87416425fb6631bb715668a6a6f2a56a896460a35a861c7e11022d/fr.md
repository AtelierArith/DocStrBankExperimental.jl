```
trunc(dt::TimeType, ::Type{Period}) -> TimeType
```

Tronque la valeur de `dt` selon le type de `Period` fourni.

# Exemples

```jldoctest
julia> trunc(DateTime("1996-01-01T12:30:00"), Day)
1996-01-01T00:00:00
```
