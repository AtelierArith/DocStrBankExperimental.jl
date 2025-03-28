```
syrk(uplo, trans, alpha, A)
```

Devuelve ya sea el triángulo superior o el triángulo inferior de `A`, de acuerdo con [`uplo`](@ref stdlib-blas-uplo), de `alpha*A*transpose(A)` o `alpha*transpose(A)*A`, de acuerdo con [`trans`](@ref stdlib-blas-trans).
