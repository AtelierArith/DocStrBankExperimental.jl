```
scal!(n, a, X, incx)
scal!(a, X)
```

Sobrescribe `X` con `a*X` para los primeros `n` elementos del arreglo `X` con paso `incx`. Devuelve `X`.

Si `n` y `incx` no se proporcionan, se utilizan `length(X)` y `stride(X,1)`.
