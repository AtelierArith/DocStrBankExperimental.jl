```
hemm(side, ul, alpha, A, B)
```

Retourne `alpha*A*B` ou `alpha*B*A` selon [`side`](@ref stdlib-blas-side). `A` est supposé être hermitien. Seule la triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisée.
