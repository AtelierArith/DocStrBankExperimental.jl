```
Dates.ISOTimeFormat
```

Describe el formato ISO8601 para un tiempo. Este es el valor predeterminado para `Dates.format` de un `Time`.

# Ejemplos

```jldoctest
julia> Dates.format(Time(12, 0, 43, 1), ISOTimeFormat)
"12:00:43.001"
```
