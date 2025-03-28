```
gbmv(trans, m, kl, ku, alpha, A, x)
```

Gibt `alpha*A*x` oder `alpha*A'*x` zurück, je nach [`trans`](@ref stdlib-blas-trans). Die Matrix `A` ist eine allgemeine Bandmatrix der Dimension `m` mal `size(A,2)` mit `kl` Unterdiagonalen und `ku` Oberdiagonalen, und `alpha` ist ein Skalar.
