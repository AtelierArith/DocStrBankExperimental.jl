```
scal(n, a, X, incx)
scal(a, X)
```

Gibt `X` zurück, skaliert mit `a` für die ersten `n` Elemente des Arrays `X` mit Schrittweite `incx`.

Wenn `n` und `incx` nicht angegeben sind, werden `length(X)` und `stride(X,1)` verwendet.
