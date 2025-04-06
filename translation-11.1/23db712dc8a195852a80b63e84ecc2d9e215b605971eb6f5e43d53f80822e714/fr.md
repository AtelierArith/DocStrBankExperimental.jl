```
syr2k!(uplo, trans, alpha, A, B, beta, C)
```

Mise à jour de rang-2k de la matrice symétrique `C` sous la forme `alpha*A*transpose(B) + alpha*B*transpose(A) + beta*C` ou `alpha*transpose(A)*B + alpha*transpose(B)*A + beta*C` selon [`trans`](@ref stdlib-blas-trans). Seul le triangle [`uplo`](@ref stdlib-blas-uplo) de `C` est utilisé. Retourne `C`.
