```
gemv!(tA, alpha, A, x, beta, y)
```

Actualiza el vector `y` como `alpha*A*x + beta*y` o `alpha*A'x + beta*y` de acuerdo con [`tA`](@ref stdlib-blas-trans). `alpha` y `beta` son escalares. Devuelve el `y` actualizado.
