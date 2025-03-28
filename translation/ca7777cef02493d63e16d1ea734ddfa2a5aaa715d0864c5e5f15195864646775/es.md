```
trsv!(ul, tA, dA, A, b)
```

Sobrescribe `b` con la solución a `A*x = b` o una de las otras dos variantes determinadas por [`tA`](@ref stdlib-blas-trans) y [`ul`](@ref stdlib-blas-uplo). [`dA`](@ref stdlib-blas-diag) determina si los valores diagonales se leen o se asumen como todos unos. Devuelve el `b` actualizado.
