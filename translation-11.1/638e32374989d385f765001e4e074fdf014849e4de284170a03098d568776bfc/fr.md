```
gemmt!(uplo, tA, tB, alpha, A, B, beta, C)
```

Met à jour la partie triangulaire inférieure ou supérieure spécifiée par [`uplo`](@ref stdlib-blas-uplo) de `C` comme `alpha*A*B + beta*C` ou les autres variantes selon [`tA`](@ref stdlib-blas-trans) et `tB`. Retourne le `C` mis à jour.

!!! compat "Julia 1.11"
    `gemmt!` nécessite au moins Julia 1.11.

