```
Dates.ISODateFormat
```

Décrit le formatage ISO8601 pour une date. C'est la valeur par défaut pour `Dates.format` d'une `Date`.

# Exemples

```jldoctest
julia> Dates.format(Date(2018, 8, 8), ISODateFormat)
"2018-08-08"
```
