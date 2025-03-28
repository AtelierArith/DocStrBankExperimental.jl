```
gemmt(uplo, tA, tB, A, B)
```

Retourne la partie triangulaire inférieure ou supérieure spécifiée par [`uplo`](@ref stdlib-blas-uplo) de `A*B` ou les trois autres variantes selon [`tA`](@ref stdlib-blas-trans) et `tB`.

!!! compat "Julia 1.11"
    `gemmt` nécessite au moins Julia 1.11.

