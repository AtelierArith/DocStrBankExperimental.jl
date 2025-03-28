```
her2k!(uplo, trans, alpha, A, B, beta, C)
```

Actualización de rango-2k de la matriz hermitiana `C` como `alpha*A*B' + alpha*B*A' + beta*C` o `alpha*A'*B + alpha*B'*A + beta*C` de acuerdo con [`trans`](@ref stdlib-blas-trans). El escalar `beta` debe ser real. Solo se utiliza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `C`. Devuelve `C`.
