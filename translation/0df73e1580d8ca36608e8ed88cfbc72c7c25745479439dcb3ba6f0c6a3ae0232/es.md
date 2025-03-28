```
symm(side, ul, alpha, A, B)
```

Devuelve `alpha*A*B` o `alpha*B*A` según [`side`](@ref stdlib-blas-side). Se asume que `A` es simétrica. Solo se utiliza el triángulo [`ul`](@ref stdlib-blas-uplo) de `A`.
