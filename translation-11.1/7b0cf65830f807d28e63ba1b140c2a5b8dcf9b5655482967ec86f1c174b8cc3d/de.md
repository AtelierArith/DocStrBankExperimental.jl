```
Dates.ISODateFormat
```

Beschreibt das ISO8601-Format für ein Datum. Dies ist der Standardwert für `Dates.format` eines `Date`.

# Beispiele

```jldoctest
julia> Dates.format(Date(2018, 8, 8), ISODateFormat)
"2018-08-08"
```
