```
herk!(uplo, trans, alpha, A, beta, C)
```

Methoden nur für komplexe Arrays. Rang-k Aktualisierung der hermiteschen Matrix `C` als `alpha*A*A' + beta*C` oder `alpha*A'*A + beta*C` gemäß [`trans`](@ref stdlib-blas-trans). Nur das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `C` wird aktualisiert. Gibt `C` zurück.
