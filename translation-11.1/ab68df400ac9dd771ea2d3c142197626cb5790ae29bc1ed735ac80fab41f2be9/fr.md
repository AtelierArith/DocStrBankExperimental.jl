```
hetri!(uplo, A, ipiv)
```

Calcule l'inverse d'une matrice hermitienne `A` en utilisant les résultats de `sytrf!`. Si `uplo = U`, la moitié supérieure de `A` est stockée. Si `uplo = L`, la moitié inférieure est stockée. `A` est écrasée par son inverse.
