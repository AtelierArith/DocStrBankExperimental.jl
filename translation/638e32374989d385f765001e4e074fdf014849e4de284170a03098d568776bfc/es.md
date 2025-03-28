```
gemmt!(uplo, tA, tB, alpha, A, B, beta, C)
```

Actualiza la parte triangular inferior o superior especificada por [`uplo`](@ref stdlib-blas-uplo) de `C` como `alpha*A*B + beta*C` o las otras variantes según [`tA`](@ref stdlib-blas-trans) y `tB`. Devuelve el `C` actualizado.

!!! compat "Julia 1.11"
    `gemmt!` requiere al menos Julia 1.11.

