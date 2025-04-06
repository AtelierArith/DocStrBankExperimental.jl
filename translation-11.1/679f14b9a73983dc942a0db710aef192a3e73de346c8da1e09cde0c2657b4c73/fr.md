```
sytrs!(uplo, A, ipiv, B)
```

Résout l'équation `A * X = B` pour une matrice symétrique `A` en utilisant les résultats de `sytrf!`. Si `uplo = U`, la moitié supérieure de `A` est stockée. Si `uplo = L`, la moitié inférieure est stockée. `B` est écrasé par la solution `X`.
