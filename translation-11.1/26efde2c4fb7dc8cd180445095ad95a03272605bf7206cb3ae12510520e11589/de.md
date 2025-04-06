```
dotc(n, X, incx, U, incy)
```

Dot-Funktion für zwei komplexe Vektoren, bestehend aus `n` Elementen des Arrays `X` mit Schrittweite `incx` und `n` Elementen des Arrays `U` mit Schrittweite `incy`, wobei der erste Vektor konjugiert wird.

# Beispiele

```jldoctest
julia> BLAS.dotc(10, fill(1.0im, 10), 1, fill(1.0+im, 20), 2)
10.0 - 10.0im
```
