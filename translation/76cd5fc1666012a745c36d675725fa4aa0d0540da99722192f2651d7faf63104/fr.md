```
trcon!(norm, uplo, diag, A)
```

Trouve le nombre de condition réciproque de la matrice triangulaire `A` (supérieure si `uplo = U`, inférieure si `uplo = L`). Si `diag = N`, `A` a des éléments diagonaux non unitaires. Si `diag = U`, tous les éléments diagonaux de `A` sont un. Si `norm = I`, le nombre de condition est trouvé dans la norme infinie. Si `norm = O` ou `1`, le nombre de condition est trouvé dans la norme un.
