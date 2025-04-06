```
Dates.ISODateFormat
```

Describe el formato ISO8601 para una fecha. Este es el valor predeterminado para `Dates.format` de un `Date`.

# Ejemplos

```jldoctest
julia> Dates.format(Date(2018, 8, 8), ISODateFormat)
"2018-08-08"
```
