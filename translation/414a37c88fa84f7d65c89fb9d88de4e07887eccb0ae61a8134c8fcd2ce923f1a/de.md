```
syrk!(uplo, trans, alpha, A, beta, C)
```

Rank-k-Aktualisierung der symmetrischen Matrix `C` als `alpha*A*transpose(A) + beta*C` oder `alpha*transpose(A)*A + beta*C` gemäß [`trans`](@ref stdlib-blas-trans). Nur das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `C` wird verwendet. Rückgabe `C`.
