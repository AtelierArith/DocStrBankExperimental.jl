```
gemv!(tA, alpha, A, x, beta, y)
```

Met à jour le vecteur `y` comme `alpha*A*x + beta*y` ou `alpha*A'x + beta*y` selon [`tA`](@ref stdlib-blas-trans). `alpha` et `beta` sont des scalaires. Retourne le `y` mis à jour.
