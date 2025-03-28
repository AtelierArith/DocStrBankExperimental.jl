```
dot(n, X, incx, Y, incy)
```

Skalarprodukt von zwei Vektoren, die aus `n` Elementen des Arrays `X` mit Schrittweite `incx` und `n` Elementen des Arrays `Y` mit Schrittweite `incy` bestehen.

# Beispiele

```jldoctest
julia> BLAS.dot(10, fill(1.0, 10), 1, fill(1.0, 20), 2)
10.0
```
