```
scal!(n, a, X, incx)
scal!(a, X)
```

Überschreibt `X` mit `a*X` für die ersten `n` Elemente des Arrays `X` mit Schrittweite `incx`. Gibt `X` zurück.

Wenn `n` und `incx` nicht angegeben sind, werden `length(X)` und `stride(X,1)` verwendet.
