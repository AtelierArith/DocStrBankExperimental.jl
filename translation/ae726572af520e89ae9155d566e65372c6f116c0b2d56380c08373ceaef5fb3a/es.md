```
syr2k(uplo, trans, alpha, A, B)
```

Devuelve el triángulo [`uplo`](@ref stdlib-blas-uplo) de `alpha*A*transpose(B) + alpha*B*transpose(A)` o `alpha*transpose(A)*B + alpha*transpose(B)*A`, de acuerdo con [`trans`](@ref stdlib-blas-trans).
