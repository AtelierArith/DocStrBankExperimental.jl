```
syrk!(uplo, trans, alpha, A, beta, C)
```

Actualización de rango-k de la matriz simétrica `C` como `alpha*A*transpose(A) + beta*C` o `alpha*transpose(A)*A + beta*C` de acuerdo con [`trans`](@ref stdlib-blas-trans). Solo se utiliza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `C`. Devuelve `C`.
