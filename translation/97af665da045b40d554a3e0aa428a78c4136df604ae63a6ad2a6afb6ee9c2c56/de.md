```
symm!(seite, ul, alpha, A, B, beta, C)
```

Aktualisiere `C` als `alpha*A*B + beta*C` oder `alpha*B*A + beta*C` gemäß [`seite`](@ref stdlib-blas-side). `A` wird als symmetrisch angenommen. Nur das [`ul`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet. Gib das aktualisierte `C` zurück.
