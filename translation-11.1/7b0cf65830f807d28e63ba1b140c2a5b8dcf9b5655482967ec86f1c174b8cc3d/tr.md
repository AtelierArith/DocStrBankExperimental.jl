```
Dates.ISODateFormat
```

Bir tarihin ISO8601 formatlamasını açıklar. Bu, bir `Date` için `Dates.format`'ın varsayılan değeridir.

# Örnekler

```jldoctest
julia> Dates.format(Date(2018, 8, 8), ISODateFormat)
"2018-08-08"
```
