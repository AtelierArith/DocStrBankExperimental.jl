```
Dates.ISODateTimeFormat
```

Décrit le format ISO8601 pour une date et une heure. C'est la valeur par défaut pour `Dates.format` d'un `DateTime`.

# Exemples

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), ISODateTimeFormat)
"2018-08-08T12:00:43.001"
```
