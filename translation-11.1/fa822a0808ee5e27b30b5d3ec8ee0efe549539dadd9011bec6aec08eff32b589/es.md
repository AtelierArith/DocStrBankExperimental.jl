```
herk!(uplo, trans, alpha, A, beta, C)
```

Métodos solo para arreglos complejos. Actualización de rango-k de la matriz Hermitiana `C` como `alpha*A*A' + beta*C` o `alpha*A'*A + beta*C` de acuerdo con [`trans`](@ref stdlib-blas-trans). Solo se actualiza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `C`. Devuelve `C`.
