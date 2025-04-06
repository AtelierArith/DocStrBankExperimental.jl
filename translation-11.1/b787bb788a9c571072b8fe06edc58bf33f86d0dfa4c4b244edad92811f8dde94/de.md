```
trmm(seite, ul, tA, dA, alpha, A, B)
```

Gibt `alpha*A*B` oder eine der anderen drei Varianten zurück, die durch [`seite`](@ref stdlib-blas-side) und [`tA`](@ref stdlib-blas-trans) bestimmt werden. Nur das [`ul`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet. [`dA`](@ref stdlib-blas-diag) bestimmt, ob die Diagonalwerte gelesen oder als alle Einsen angenommen werden.
