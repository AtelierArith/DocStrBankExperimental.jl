```
symm(side, ul, A, B)
```

Devuelve `A*B` o `B*A` según [`side`](@ref stdlib-blas-side). Se asume que `A` es simétrica. Solo se utiliza el triángulo [`ul`](@ref stdlib-blas-uplo) de `A`.
