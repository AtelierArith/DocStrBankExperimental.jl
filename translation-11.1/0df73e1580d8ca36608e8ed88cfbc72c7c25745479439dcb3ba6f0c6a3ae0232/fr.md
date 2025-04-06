```
symm(côté, ul, alpha, A, B)
```

Retourne `alpha*A*B` ou `alpha*B*A` selon [`side`](@ref stdlib-blas-side). `A` est supposé être symétrique. Seul le triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisé.
