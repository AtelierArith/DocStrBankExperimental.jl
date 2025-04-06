```
hemm(side, ul, A, B)
```

Retourne `A*B` ou `B*A` selon [`side`](@ref stdlib-blas-side). `A` est supposé être hermitien. Seul le triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisé.
