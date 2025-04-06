```
gbtrs!(trans, kl, ku, m, AB, ipiv, B)
```

Résoudre l'équation `AB * X = B`. `trans` détermine l'orientation de `AB`. Il peut être `N` (pas de transposition), `T` (transposition) ou `C` (transposition conjuguée). `kl` est la première sous-diagonale contenant une bande non nulle, `ku` est la dernière superdiagonale contenant une, et `m` est la première dimension de la matrice `AB`. `ipiv` est le vecteur de pivots retourné par `gbtrf!`. Renvoie le vecteur ou la matrice `X`, écrasant `B` sur place.
