```
gemmt(uplo, tA, tB, alpha, A, B)
```

Devuelve la parte triangular inferior o superior especificada por [`uplo`](@ref stdlib-blas-uplo) de `A*B` o las otras tres variantes según [`tA`](@ref stdlib-blas-trans) y `tB`.

!!! compat "Julia 1.11"
    `gemmt` requiere al menos Julia 1.11.

