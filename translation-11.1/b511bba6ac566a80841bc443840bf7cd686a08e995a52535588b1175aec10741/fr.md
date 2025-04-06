```
her2k!(uplo, trans, alpha, A, B, beta, C)
```

Mise à jour de rang-2k de la matrice hermitienne `C` sous la forme `alpha*A*B' + alpha*B*A' + beta*C` ou `alpha*A'*B + alpha*B'*A + beta*C` selon [`trans`](@ref stdlib-blas-trans). Le scalaire `beta` doit être réel. Seut le triangle [`uplo`](@ref stdlib-blas-uplo) de `C` est utilisé. Retourne `C`.
