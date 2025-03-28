```
sbmv(uplo, k, alpha, A, x)
```

Retourne `alpha*A*x` où `A` est une matrice symétrique en bande d'ordre `size(A,2)` avec `k` super-diagonales stockées dans l'argument `A`. Seul le triangle [`uplo`](@ref stdlib-blas-uplo) de `A` est utilisé.
