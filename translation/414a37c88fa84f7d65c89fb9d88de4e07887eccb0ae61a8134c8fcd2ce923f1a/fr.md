```
syrk!(uplo, trans, alpha, A, beta, C)
```

Mise à jour de rang-k de la matrice symétrique `C` sous la forme `alpha*A*transpose(A) + beta*C` ou `alpha*transpose(A)*A + beta*C` selon [`trans`](@ref stdlib-blas-trans). Seul le triangle [`uplo`](@ref stdlib-blas-uplo) de `C` est utilisé. Retourne `C`.
