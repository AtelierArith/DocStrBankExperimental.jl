```
pttrs!(D, E, B)
```

Résout `A * X = B` pour `A` tridiagonale définie positive avec la diagonale `D` et les éléments hors diagonale `E` après avoir calculé la factorisation LDLt de `A` en utilisant `pttrf!`. `B` est écrasé avec la solution `X`.
