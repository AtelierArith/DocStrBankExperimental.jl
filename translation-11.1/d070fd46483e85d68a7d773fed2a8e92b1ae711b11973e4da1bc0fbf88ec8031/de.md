```
hemv!(ul, alpha, A, x, beta, y)
```

Aktualisiere den Vektor `y` als `alpha*A*x + beta*y`. `A` wird als hermitesch angenommen. Nur das [`ul`](@ref stdlib-blas-uplo) Dreieck von `A` wird verwendet. `alpha` und `beta` sind Skalare. Gib das aktualisierte `y` zurück.
