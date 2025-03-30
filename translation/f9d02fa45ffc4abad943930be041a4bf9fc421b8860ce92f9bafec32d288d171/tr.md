```
bitrand([rng=default_rng()], [dims...])
```

Rastgele boolean değerlerden oluşan bir `BitArray` oluşturur.

# Örnekler

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
