```
gbmv(trans, m, kl, ku, alpha, A, x)
```

Devuelve `alpha*A*x` o `alpha*A'*x` según [`trans`](@ref stdlib-blas-trans). La matriz `A` es una matriz de banda general de dimensión `m` por `size(A,2)` con `kl` sub-diagonales y `ku` super-diagonales, y `alpha` es un escalar.
