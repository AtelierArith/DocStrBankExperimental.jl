```
nrm2(n, X, incx)
```

`X` dizisindeki `n` elemandan oluşan bir vektörün 2-normu, `incx` adımı ile.

# Örnekler

```jldoctest
julia> BLAS.nrm2(4, fill(1.0, 8), 2)
2.0

julia> BLAS.nrm2(1, fill(1.0, 8), 2)
1.0
```
