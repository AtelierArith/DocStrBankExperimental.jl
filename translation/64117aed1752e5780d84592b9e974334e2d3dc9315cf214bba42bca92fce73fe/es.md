```
nrm2(n, X, incx)
```

2-norma de un vector que consiste en `n` elementos del arreglo `X` con paso `incx`.

# Ejemplos

```jldoctest
julia> BLAS.nrm2(4, fill(1.0, 8), 2)
2.0

julia> BLAS.nrm2(1, fill(1.0, 8), 2)
1.0
```
