```
gbmv!(trans, m, kl, ku, alpha, A, x, beta, y)
```

Actualiza el vector `y` como `alpha*A*x + beta*y` o `alpha*A'*x + beta*y` de acuerdo con [`trans`](@ref stdlib-blas-trans). La matriz `A` es una matriz de banda general de dimensión `m` por `size(A,2)` con `kl` sub-diagonales y `ku` super-diagonales. `alpha` y `beta` son escalares. Devuelve el `y` actualizado.
