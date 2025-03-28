```
nrm2(n, X, incx)
```

2-norme d'un vecteur composé de `n` éléments du tableau `X` avec un pas `incx`.

# Exemples

```jldoctest
julia> BLAS.nrm2(4, fill(1.0, 8), 2)
2.0

julia> BLAS.nrm2(1, fill(1.0, 8), 2)
1.0
```
