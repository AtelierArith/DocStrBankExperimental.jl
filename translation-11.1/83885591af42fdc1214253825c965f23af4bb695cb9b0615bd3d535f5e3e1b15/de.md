```
issubnormal(f) -> Bool
```

Testen, ob eine Fließkommazahl subnormal ist.

Eine IEEE-Fließkommazahl ist [subnormal](https://en.wikipedia.org/wiki/Subnormal_number), wenn ihre Exponentenbits null sind und ihr Signifikand nicht null ist.

# Beispiele

```jldoctest
julia> floatmin(Float32)
1.1754944f-38

julia> issubnormal(1.0f-37)
false

julia> issubnormal(1.0f-38)
true
```
