```
gbmv(trans, m, kl, ku, alpha, A, x)
```

Retourne `alpha*A*x` ou `alpha*A'*x` selon [`trans`](@ref stdlib-blas-trans). La matrice `A` est une matrice bande générale de dimension `m` par `size(A,2)` avec `kl` sous-diagonales et `ku` super-diagonales, et `alpha` est un scalaire.
