```
trmm!(côté, ul, tA, dA, alpha, A, B)
```

Mettez à jour `B` en tant que `alpha*A*B` ou l'une des trois autres variantes déterminées par [`côté`](@ref stdlib-blas-side) et [`tA`](@ref stdlib-blas-trans). Seul le triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisé. [`dA`](@ref stdlib-blas-diag) détermine si les valeurs diagonales sont lues ou supposées être toutes égales à un. Retournez le `B` mis à jour.
