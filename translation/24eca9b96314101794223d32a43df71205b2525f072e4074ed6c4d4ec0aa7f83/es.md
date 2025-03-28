```
scal(n, a, X, incx)
scal(a, X)
```

Devuelve `X` escalado por `a` para los primeros `n` elementos del arreglo `X` con un paso de `incx`.

Si `n` e `incx` no se proporcionan, se utilizan `length(X)` y `stride(X,1)`.
