```
expm1(x)
```

Berechnet genau $e^x-1$. Es vermeidet den Verlust an Präzision, der bei der direkten Auswertung von exp(x)-1 für kleine Werte von x auftritt.

# Beispiele

```jldoctest
julia> expm1(1e-16)
1.0e-16

julia> exp(1e-16) - 1
0.0
```
