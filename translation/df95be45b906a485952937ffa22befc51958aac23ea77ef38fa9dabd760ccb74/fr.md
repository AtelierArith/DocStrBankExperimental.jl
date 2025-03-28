```
dotu(n, X, incx, Y, incy)
```

Fonction Dot pour deux vecteurs complexes consistant en `n` éléments du tableau `X` avec un pas `incx` et `n` éléments du tableau `Y` avec un pas `incy`.

# Exemples

```jldoctest
julia> BLAS.dotu(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
-10.0 + 10.0im
```
