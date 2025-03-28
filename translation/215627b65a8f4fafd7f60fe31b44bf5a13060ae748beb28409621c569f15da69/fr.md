```
trsm(côté, ul, tA, dA, alpha, A, B)
```

Retourne la solution de `A*X = alpha*B` ou l'une des trois autres variantes déterminées par [`side`](@ref stdlib-blas-side) et [`tA`](@ref stdlib-blas-trans). Seul le triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisé. [`dA`](@ref stdlib-blas-diag) détermine si les valeurs diagonales sont lues ou supposées être toutes égales à un.
