```
hemv!(ul, alpha, A, x, beta, y)
```

Actualiza el vector `y` como `alpha*A*x + beta*y`. Se asume que `A` es Hermitiana. Solo se utiliza el triángulo [`ul`](@ref stdlib-blas-uplo) de `A`. `alpha` y `beta` son escalares. Devuelve el `y` actualizado.
