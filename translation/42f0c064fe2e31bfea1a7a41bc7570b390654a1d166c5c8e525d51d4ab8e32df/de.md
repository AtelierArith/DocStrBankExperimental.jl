```
rot!(n, X, incx, Y, incy, c, s)
```

Überschreibt `X` mit `c*X + s*Y` und `Y` mit `-conj(s)*X + c*Y` für die ersten `n` Elemente des Arrays `X` mit Schrittweite `incx` und die ersten `n` Elemente des Arrays `Y` mit Schrittweite `incy`. Gibt `X` und `Y` zurück.

!!! compat "Julia 1.5"
    `rot!` erfordert mindestens Julia 1.5.

