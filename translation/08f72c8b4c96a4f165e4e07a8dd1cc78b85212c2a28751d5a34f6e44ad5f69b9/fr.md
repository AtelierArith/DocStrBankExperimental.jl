```
sbmv(uplo, k, A, x)
```

Retourne `A*x` où `A` est une matrice symétrique en bande d'ordre `size(A,2)` avec `k` super-diagonales stockées dans l'argument `A`. Seule la triangle [`uplo`](@ref stdlib-blas-uplo) de `A` est utilisée.
