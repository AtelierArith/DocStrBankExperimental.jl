```
trsyl!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

Résout l'équation matricielle de Sylvester `A * X +/- X * B = scale*C` où `A` et `B` sont tous deux quasi-triangulaires supérieurs. Si `transa = N`, `A` n'est pas modifié. Si `transa = T`, `A` est transposé. Si `transa = C`, `A` est conjugué transposé. De même pour `transb` et `B`. Si `isgn = 1`, l'équation `A * X + X * B = scale * C` est résolue. Si `isgn = -1`, l'équation `A * X - X * B = scale * C` est résolue.

Renvoie `X` (écrasant `C`) et `scale`.
