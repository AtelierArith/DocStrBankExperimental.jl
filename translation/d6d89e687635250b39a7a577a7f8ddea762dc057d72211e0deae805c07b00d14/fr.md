```
asum(n, X, incx)
```

Somme des magnitudes des premiers `n` éléments du tableau `X` avec un pas `incx`.

Pour un tableau réel, la magnitude est la valeur absolue. Pour un tableau complexe, la magnitude est la somme de la valeur absolue de la partie réelle et de la valeur absolue de la partie imaginaire.

# Exemples

```jldoctest
julia> BLAS.asum(5, fill(1.0im, 10), 2)
5.0

julia> BLAS.asum(2, fill(1.0im, 10), 5)
2.0
```
