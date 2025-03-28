```
syr2k!(uplo, trans, alpha, A, B, beta, C)
```

Rank-2k-Aktualisierung der symmetrischen Matrix `C` als `alpha*A*transpose(B) + alpha*B*transpose(A) + beta*C` oder `alpha*transpose(A)*B + alpha*transpose(B)*A + beta*C` gemäß [`trans`](@ref stdlib-blas-trans). Nur das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `C` wird verwendet. Gibt `C` zurück.
