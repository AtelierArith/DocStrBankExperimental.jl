```
sbmv(uplo, k, A, x)
```

Devuelve `A*x` donde `A` es una matriz de banda simétrica de orden `size(A,2)` con `k` superdiagonales almacenadas en el argumento `A`. Solo se utiliza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `A`.
