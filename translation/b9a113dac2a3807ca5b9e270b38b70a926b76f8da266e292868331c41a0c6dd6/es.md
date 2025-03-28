```
syr!(uplo, alpha, x, A)
```

Actualización de rango-1 de la matriz simétrica `A` con el vector `x` como `alpha*x*transpose(x) + A`. [`uplo`](@ref stdlib-blas-uplo) controla qué triángulo de `A` se actualiza. Devuelve `A`.
