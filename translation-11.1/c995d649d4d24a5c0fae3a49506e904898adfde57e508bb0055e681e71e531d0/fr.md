```
hesv!(uplo, A, B) -> (B, A, ipiv)
```

Trouve la solution de `A * X = B` pour la matrice hermitienne `A`. Si `uplo = U`, la moitié supérieure de `A` est stockée. Si `uplo = L`, la moitié inférieure est stockée. `B` est écrasé par la solution `X`. `A` est écrasé par sa factorisation de Bunch-Kaufman. `ipiv` contient des informations de pivotage sur la factorisation.
