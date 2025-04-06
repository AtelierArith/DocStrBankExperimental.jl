```
Dates.RFC1123Format
```

Beschreibt das RFC1123-Format für ein Datum und eine Uhrzeit.

# Beispiele

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), RFC1123Format)
"Wed, 08 Aug 2018 12:00:43"
```
