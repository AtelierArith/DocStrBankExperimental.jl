```
gemm!(tA, tB, alpha, A, B, beta, C)
```

Aktualisiere `C` als `alpha*A*B + beta*C` oder die anderen drei Varianten gemäß [`tA`](@ref stdlib-blas-trans) und `tB`. Gib das aktualisierte `C` zurück.
