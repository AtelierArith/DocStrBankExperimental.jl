```
sbmv(uplo, k, alpha, A, x)
```

Devuelve `alpha*A*x` donde `A` es una matriz de banda simétrica de orden `size(A,2)` con `k` super-diagonales almacenadas en el argumento `A`. Solo se utiliza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `A`.
