```
trtri!(uplo, diag, A)
```

Trouve l'inverse de la matrice triangulaire `A` (supérieure si `uplo = U`, inférieure si `uplo = L`). Si `diag = N`, `A` a des éléments diagonaux non unitaires. Si `diag = U`, tous les éléments diagonaux de `A` sont un. `A` est écrasé avec son inverse.
