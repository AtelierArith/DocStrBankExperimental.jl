```
syrk(uplo, trans, alpha, A)
```

Retourne soit le triangle supérieur soit le triangle inférieur de `A`, selon [`uplo`](@ref stdlib-blas-uplo), de `alpha*A*transpose(A)` ou `alpha*transpose(A)*A`, selon [`trans`](@ref stdlib-blas-trans).
