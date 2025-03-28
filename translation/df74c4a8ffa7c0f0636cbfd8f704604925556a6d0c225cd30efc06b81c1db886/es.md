```
Dates.RFC1123Format
```

Describe el formato RFC1123 para una fecha y hora.

# Ejemplos

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), RFC1123Format)
"Wed, 08 Aug 2018 12:00:43"
```
