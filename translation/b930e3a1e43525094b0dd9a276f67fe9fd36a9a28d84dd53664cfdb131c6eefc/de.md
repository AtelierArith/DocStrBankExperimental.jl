```
gbmv!(trans, m, kl, ku, alpha, A, x, beta, y)
```

Aktualisiere den Vektor `y` als `alpha*A*x + beta*y` oder `alpha*A'*x + beta*y` gemäß [`trans`](@ref stdlib-blas-trans). Die Matrix `A` ist eine allgemeine Bandmatrix der Dimension `m` mal `size(A,2)` mit `kl` Unterdiagonalen und `ku` Oberdiagonalen. `alpha` und `beta` sind Skalare. Gib das aktualisierte `y` zurück.
