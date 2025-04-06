```
her2k!(uplo, trans, alpha, A, B, beta, C)
```

Rank-2k-Aktualisierung der hermiteschen Matrix `C` als `alpha*A*B' + alpha*B*A' + beta*C` oder `alpha*A'*B + alpha*B'*A + beta*C` gemäß [`trans`](@ref stdlib-blas-trans). Der Skalar `beta` muss reell sein. Nur das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `C` wird verwendet. Rückgabe `C`.
