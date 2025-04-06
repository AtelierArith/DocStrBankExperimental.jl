```
geqp3!(A, [jpvt, tau]) -> (A, tau, jpvt)
```

Calculez la factorisation `QR` pivotée de `A`, `AP = QR` en utilisant BLAS niveau 3. `P` est une matrice de pivotement, représentée par `jpvt`. `tau` stocke les réflecteurs élémentaires. Les arguments `jpvt` et `tau` sont optionnels et permettent de passer des tableaux préalloués. Lorsqu'ils sont passés, `jpvt` doit avoir une longueur supérieure ou égale à `n` si `A` est une matrice `(m x n)` et `tau` doit avoir une longueur supérieure ou égale à la plus petite dimension de `A`. À l'entrée, si `jpvt[j]` n'est pas égal à zéro, alors la `j`-ème colonne de `A` est permutée au début de `AP`.

`A`, `jpvt` et `tau` sont modifiés sur place.
