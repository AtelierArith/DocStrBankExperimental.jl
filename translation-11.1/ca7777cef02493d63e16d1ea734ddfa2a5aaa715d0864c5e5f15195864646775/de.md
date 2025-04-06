```
trsv!(ul, tA, dA, A, b)
```

Überschreibe `b` mit der Lösung von `A*x = b` oder einer der anderen beiden Varianten, die durch [`tA`](@ref stdlib-blas-trans) und [`ul`](@ref stdlib-blas-uplo) bestimmt werden. [`dA`](@ref stdlib-blas-diag) bestimmt, ob die Diagonalwerte gelesen oder als alle Einsen angenommen werden. Gib das aktualisierte `b` zurück.
