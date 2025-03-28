```
dot(n, X, incx, Y, incy)
```

Produit scalaire de deux vecteurs consistant en `n` éléments du tableau `X` avec un pas `incx` et `n` éléments du tableau `Y` avec un pas `incy`.

# Exemples

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
