```
herk!(uplo, trans, alpha, A, beta, C)
```

Méthodes uniquement pour les tableaux complexes. Mise à jour de rang-k de la matrice hermitienne `C` sous la forme `alpha*A*A' + beta*C` ou `alpha*A'*A + beta*C` selon [`trans`](@ref stdlib-blas-trans). Seul le triangle [`uplo`](@ref stdlib-blas-uplo) de `C` est mis à jour. Renvoie `C`.
