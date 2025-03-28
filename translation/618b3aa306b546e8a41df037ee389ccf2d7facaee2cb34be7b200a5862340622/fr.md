```
gels!(trans, A, B) -> (F, B, ssr)
```

Résout l'équation linéaire `A * X = B`, `transpose(A) * X = B`, ou `adjoint(A) * X = B` en utilisant une factorisation QR ou LQ. Modifie la matrice/vecteur `B` sur place avec la solution. `A` est écrasé avec sa factorisation `QR` ou `LQ`. `trans` peut être l'un de `N` (aucune modification), `T` (transposée), ou `C` (transposée conjuguée). `gels!` recherche la solution de norme minimale/moins carrés. `A` peut être sous ou sur déterminé. La solution est renvoyée dans `B`.
