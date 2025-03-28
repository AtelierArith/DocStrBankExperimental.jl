```
syr2k!(uplo, trans, alpha, A, B, beta, C)
```

Actualización de rango-2k de la matriz simétrica `C` como `alpha*A*transpose(B) + alpha*B*transpose(A) + beta*C` o `alpha*transpose(A)*B + alpha*transpose(B)*A + beta*C` de acuerdo con [`trans`](@ref stdlib-blas-trans). Solo se utiliza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `C`. Devuelve `C`.
