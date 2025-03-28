```
trsm(seite, ul, tA, dA, alpha, A, B)
```

Geben Sie die Lösung für `A*X = alpha*B` oder eine der anderen drei Varianten zurück, die durch [`seite`](@ref stdlib-blas-side) und [`tA`](@ref stdlib-blas-trans) bestimmt werden. Nur das [`ul`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet. [`dA`](@ref stdlib-blas-diag) bestimmt, ob die Diagonalwerte gelesen oder als Einsen angenommen werden.
