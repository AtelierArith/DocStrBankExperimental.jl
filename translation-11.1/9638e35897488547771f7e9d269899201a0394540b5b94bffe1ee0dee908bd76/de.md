```
trmm!(seite, ul, tA, dA, alpha, A, B)
```

Aktualisiere `B` als `alpha*A*B` oder eine der anderen drei Varianten, die durch [`seite`](@ref stdlib-blas-side) und [`tA`](@ref stdlib-blas-trans) bestimmt werden. Nur das [`ul`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet. [`dA`](@ref stdlib-blas-diag) bestimmt, ob die Diagonalwerte gelesen oder als alle Einsen angenommen werden. Gib das aktualisierte `B` zurück.
