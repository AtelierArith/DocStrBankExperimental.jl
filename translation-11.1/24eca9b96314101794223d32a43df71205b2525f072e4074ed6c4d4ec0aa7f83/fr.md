```
scal(n, a, X, incx)
scal(a, X)
```

Renvoie `X` mis à l'échelle par `a` pour les premiers `n` éléments du tableau `X` avec un pas `incx`.

Si `n` et `incx` ne sont pas fournis, `length(X)` et `stride(X,1)` sont utilisés.
