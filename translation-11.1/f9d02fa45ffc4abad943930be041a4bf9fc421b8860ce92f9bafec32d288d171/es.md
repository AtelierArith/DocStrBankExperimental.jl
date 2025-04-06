```
bitrand([rng=default_rng()], [dims...])
```

Genera un `BitArray` de valores booleanos aleatorios.

# Ejemplos

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
