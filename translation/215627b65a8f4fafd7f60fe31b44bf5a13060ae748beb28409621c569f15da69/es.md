```
trsm(lado, ul, tA, dA, alpha, A, B)
```

Devuelve la solución a `A*X = alpha*B` o una de las otras tres variantes determinadas por [`lado`](@ref stdlib-blas-side) y [`tA`](@ref stdlib-blas-trans). Solo se utiliza el triángulo [`ul`](@ref stdlib-blas-uplo) de `A`. [`dA`](@ref stdlib-blas-diag) determina si los valores diagonales se leen o se asumen todos como uno.
