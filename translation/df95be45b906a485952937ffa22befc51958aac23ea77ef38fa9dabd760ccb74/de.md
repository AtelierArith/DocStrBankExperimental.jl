```
dotu(n, X, incx, Y, incy)
```

Dot-Funktion für zwei komplexe Vektoren, die aus `n` Elementen des Arrays `X` mit Schrittweite `incx` und `n` Elementen des Arrays `Y` mit Schrittweite `incy` bestehen.

# Beispiele

```jldoctest
julia> BLAS.dotu(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
-10.0 + 10.0im
```
