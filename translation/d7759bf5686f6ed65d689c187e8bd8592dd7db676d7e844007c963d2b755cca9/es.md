```
sbmv!(uplo, k, alpha, A, x, beta, y)
```

Actualiza el vector `y` como `alpha*A*x + beta*y` donde `A` es una matriz simétrica en banda de orden `size(A,2)` con `k` superdiagonales almacenadas en el argumento `A`. El diseño de almacenamiento para `A` se describe en el módulo de referencia BLAS, BLAS de nivel 2 en [https://www.netlib.org/lapack/explore-html/](https://www.netlib.org/lapack/explore-html/). Solo se utiliza el triángulo [`uplo`](@ref stdlib-blas-uplo) de `A`.

Devuelve el `y` actualizado.
