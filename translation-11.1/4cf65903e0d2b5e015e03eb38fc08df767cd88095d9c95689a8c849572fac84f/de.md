```
Dates.ISODateTimeFormat
```

Beschreibt das ISO8601-Format für ein Datum und eine Uhrzeit. Dies ist der Standardwert für `Dates.format` eines `DateTime`.

# Beispiele

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), ISODateTimeFormat)
"2018-08-08T12:00:43.001"
```
