```
bitrand([rng=default_rng()], [dims...])
```

Generiert ein `BitArray` mit zufälligen booleschen Werten.

# Beispiele

```jldoctest
julia> bitrand(Xoshiro(123), 10)
10-element BitVector:
 0
 1
 0
 1
 0
 1
 0
 0
 1
 1
```
