```
dotc(n, X, incx, U, incy)
```

Fonction Dot pour deux vecteurs complexes, consistant en `n` éléments du tableau `X` avec un pas `incx` et `n` éléments du tableau `U` avec un pas `incy`, conjuguant le premier vecteur.

# Exemples

```jldoctest
julia> BLAS.dotc(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
10.0 - 10.0im
```
