```
Dates.ISOTimeFormat
```

Décrit le format ISO8601 pour une heure. C'est la valeur par défaut pour `Dates.format` d'un `Time`.

# Exemples

```jldoctest
julia> Dates.format(Time(12, 0, 43, 1), ISOTimeFormat)
"12:00:43.001"
```
