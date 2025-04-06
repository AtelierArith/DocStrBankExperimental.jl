```
Dates.ISOTimeFormat
```

Beschreibt das ISO8601-Format für eine Zeit. Dies ist der Standardwert für `Dates.format` eines `Time`.

# Beispiele

```jldoctest
julia> Dates.format(Time(12, 0, 43, 1), ISOTimeFormat)
"12:00:43.001"
```
