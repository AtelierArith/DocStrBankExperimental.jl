```
syconv!(uplo, A, ipiv) -> (A, work)
```

Convertit une matrice symétrique `A` (qui a été factorisée en une matrice triangulaire) en deux matrices `L` et `D`. Si `uplo = U`, `A` est triangulaire supérieure. Si `uplo = L`, elle est triangulaire inférieure. `ipiv` est le vecteur de pivot de la factorisation triangulaire. `A` est écrasée par `L` et `D`.
