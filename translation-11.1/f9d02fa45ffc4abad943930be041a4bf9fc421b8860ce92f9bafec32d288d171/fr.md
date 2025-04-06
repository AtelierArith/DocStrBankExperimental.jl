```
bitrand([rng=default_rng()], [dims...])
```

Génère un `BitArray` de valeurs booléennes aléatoires.

# Exemples

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
