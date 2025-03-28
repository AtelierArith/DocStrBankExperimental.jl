```
gbtrf!(kl, ku, m, AB) -> (AB, ipiv)
```

Calculez la factorisation LU d'une matrice en bande `AB`. `kl` est la première sous-diagonale contenant une bande non nulle, `ku` est la dernière superdiagonale contenant une bande, et `m` est la première dimension de la matrice `AB`. Renvoie la factorisation LU sur place et `ipiv`, le vecteur de pivots utilisés.
