```
potri!(uplo, A)
```

Calcule l'inverse de la matrice définie positive `A` après avoir appelé `potrf!` pour trouver sa décomposition de Cholesky (supérieure si `uplo = U`, inférieure si `uplo = L`).

`A` est écrasée par son inverse et retournée.
