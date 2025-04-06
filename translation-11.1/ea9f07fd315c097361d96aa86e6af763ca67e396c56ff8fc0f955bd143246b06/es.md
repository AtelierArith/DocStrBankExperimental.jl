```
her!(uplo, alpha, x, A)
```

Métodos solo para arreglos complejos. Actualización de rango 1 de la matriz Hermitiana `A` con el vector `x` como `alpha*x*x' + A`. [`uplo`](@ref stdlib-blas-uplo) controla qué triángulo de `A` se actualiza. Devuelve `A`.
