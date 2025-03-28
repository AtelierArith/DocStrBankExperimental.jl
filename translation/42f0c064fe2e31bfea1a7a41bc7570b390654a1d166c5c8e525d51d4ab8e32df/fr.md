```
rot!(n, X, incx, Y, incy, c, s)
```

Écrase `X` avec `c*X + s*Y` et `Y` avec `-conj(s)*X + c*Y` pour les premiers `n` éléments du tableau `X` avec un pas `incx` et les premiers `n` éléments du tableau `Y` avec un pas `incy`. Renvoie `X` et `Y`.

!!! compat "Julia 1.5"
    `rot!` nécessite au moins Julia 1.5.

