```
ormrz!(côté, trans, A, tau, C)
```

Multiplie la matrice `C` par `Q` à partir de la transformation fournie par `tzrzf!`. Selon `côté` ou `trans`, la multiplication peut être à gauche (`côté = L, Q*C`) ou à droite (`côté = R, C*Q`) et `Q` peut être non modifié (`trans = N`), transposé (`trans = T`), ou conjugué transposé (`trans = C`). Renvoie la matrice `C` qui est modifiée en place avec le résultat de la multiplication.
