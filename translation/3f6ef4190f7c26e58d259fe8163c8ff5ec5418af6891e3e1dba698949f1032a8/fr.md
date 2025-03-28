```
gemm!(tA, tB, alpha, A, B, beta, C)
```

Mettre à jour `C` comme `alpha*A*B + beta*C` ou les trois autres variantes selon [`tA`](@ref stdlib-blas-trans) et `tB`. Retourner le `C` mis à jour.
