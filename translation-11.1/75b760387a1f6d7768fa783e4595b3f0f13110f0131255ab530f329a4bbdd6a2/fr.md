```
symv!(ul, alpha, A, x, beta, y)
```

Met à jour le vecteur `y` comme `alpha*A*x + beta*y`. `A` est supposé être symétrique. Seule la triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisée. `alpha` et `beta` sont des scalaires. Retourne le `y` mis à jour.
