```
sbmv(uplo, k, A, x)
```

Gibt `A*x` zurück, wobei `A` eine symmetrische Bandmatrix der Ordnung `size(A,2)` mit `k` Superdiagonalen ist, die im Argument `A` gespeichert sind. Nur das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet.
