```
sbmv!(uplo, k, alpha, A, x, beta, y)
```

Met à jour le vecteur `y` comme `alpha*A*x + beta*y` où `A` est une matrice symétrique en bande d'ordre `size(A,2)` avec `k` super-diagonales stockées dans l'argument `A`. La disposition de stockage pour `A` est décrite dans le module de référence BLAS, BLAS de niveau 2 à [https://www.netlib.org/lapack/explore-html/](https://www.netlib.org/lapack/explore-html/). Seul le triangle [`uplo`](@ref stdlib-blas-uplo) de `A` est utilisé.

Retourne le `y` mis à jour.
