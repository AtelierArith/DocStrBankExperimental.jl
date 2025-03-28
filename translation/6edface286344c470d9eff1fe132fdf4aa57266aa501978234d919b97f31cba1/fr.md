```
hemm!(côté, ul, alpha, A, B, beta, C)
```

Mettez à jour `C` en tant que `alpha*A*B + beta*C` ou `alpha*B*A + beta*C` selon [`côté`](@ref stdlib-blas-side). `A` est supposé être hermitien. Seul le triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisé. Retournez le `C` mis à jour.
