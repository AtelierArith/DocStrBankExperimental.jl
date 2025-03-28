```
trmv!(ul, tA, dA, A, b)
```

Devuelve `op(A)*b`, donde `op` está determinado por [`tA`](@ref stdlib-blas-trans). Solo se utiliza el triángulo [`ul`](@ref stdlib-blas-uplo) de `A`. [`dA`](@ref stdlib-blas-diag) determina si los valores diagonales se leen o se asumen todos como uno. La multiplicación ocurre en su lugar en `b`.
