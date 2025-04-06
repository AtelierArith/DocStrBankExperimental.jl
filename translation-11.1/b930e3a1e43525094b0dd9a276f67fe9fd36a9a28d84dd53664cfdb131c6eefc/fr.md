```
gbmv!(trans, m, kl, ku, alpha, A, x, beta, y)
```

Met à jour le vecteur `y` comme `alpha*A*x + beta*y` ou `alpha*A'*x + beta*y` selon [`trans`](@ref stdlib-blas-trans). La matrice `A` est une matrice bande générale de dimension `m` par `size(A,2)` avec `kl` sous-diagonales et `ku` super-diagonales. `alpha` et `beta` sont des scalaires. Retourne le `y` mis à jour.
