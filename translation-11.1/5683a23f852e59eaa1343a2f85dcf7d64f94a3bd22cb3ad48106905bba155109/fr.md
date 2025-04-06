```
sytrf!(uplo, A) -> (A, ipiv, info)
```

Calcule la factorisation de Bunch-Kaufman d'une matrice symétrique `A`. Si `uplo = U`, la moitié supérieure de `A` est stockée. Si `uplo = L`, la moitié inférieure est stockée.

Renvoie `A`, écrasée par la factorisation, un vecteur de pivots `ipiv`, et le code d'erreur `info` qui est un entier non négatif. Si `info` est positif, la matrice est singulière et la partie diagonale de la factorisation est exactement zéro à la position `info`.
