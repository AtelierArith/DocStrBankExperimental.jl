```
symm!(lado, ul, alpha, A, B, beta, C)
```

Actualiza `C` como `alpha*A*B + beta*C` o `alpha*B*A + beta*C` de acuerdo a [`lado`](@ref stdlib-blas-side). Se asume que `A` es simétrica. Solo se utiliza el triángulo [`ul`](@ref stdlib-blas-uplo) de `A`. Devuelve el `C` actualizado.
