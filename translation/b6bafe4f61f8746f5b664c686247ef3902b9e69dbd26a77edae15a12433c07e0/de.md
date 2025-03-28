```
trmv!(ul, tA, dA, A, b)
```

Gibt `op(A)*b` zurück, wobei `op` durch [`tA`](@ref stdlib-blas-trans) bestimmt wird. Nur das [`ul`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet. [`dA`](@ref stdlib-blas-diag) bestimmt, ob die Diagonalwerte gelesen oder als alle Einsen angenommen werden. Die Multiplikation erfolgt in-place auf `b`.
