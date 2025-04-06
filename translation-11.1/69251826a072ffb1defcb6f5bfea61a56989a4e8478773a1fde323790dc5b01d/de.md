```
gemv!(tA, alpha, A, x, beta, y)
```

Aktualisiere den Vektor `y` als `alpha*A*x + beta*y` oder `alpha*A'x + beta*y` gemäß [`tA`](@ref stdlib-blas-trans). `alpha` und `beta` sind Skalare. Gib das aktualisierte `y` zurück.
