```
nrm2(n, X, incx)
```

2-Norm eines Vektors, der aus `n` Elementen des Arrays `X` mit Schrittweite `incx` besteht.

# Beispiele

```jldoctest
julia> BLAS.nrm2(4, fill(1.0, 8), 2)
2.0

julia> BLAS.nrm2(1, fill(1.0, 8), 2)
1.0
```
