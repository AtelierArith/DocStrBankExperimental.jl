```
scal!(n, a, X, incx)
scal!(a, X)
```

Écrasez `X` avec `a*X` pour les premiers `n` éléments du tableau `X` avec un pas `incx`. Renvoie `X`.

Si `n` et `incx` ne sont pas fournis, `length(X)` et `stride(X,1)` sont utilisés.
