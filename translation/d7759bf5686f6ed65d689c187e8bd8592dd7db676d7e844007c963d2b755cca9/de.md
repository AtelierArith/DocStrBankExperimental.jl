```
sbmv!(uplo, k, alpha, A, x, beta, y)
```

Aktualisiere den Vektor `y` als `alpha*A*x + beta*y`, wobei `A` eine symmetrische Bandmatrix der Ordnung `size(A,2)` mit `k` Überdiagonalen ist, die im Argument `A` gespeichert sind. Das Speicherlayout für `A` wird im Referenz-BLAS-Modul, Level-2 BLAS unter [https://www.netlib.org/lapack/explore-html/](https://www.netlib.org/lapack/explore-html/) beschrieben. Nur das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet.

Gib das aktualisierte `y` zurück.
