```
Dates.ISODateTimeFormat
```

Describe el formato ISO8601 para una fecha y hora. Este es el valor predeterminado para `Dates.format` de un `DateTime`.

# Ejemplos

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), ISODateTimeFormat)
"2018-08-08T12:00:43.001"
```
