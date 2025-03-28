```
gttrs!(trans, dl, d, du, du2, ipiv, B)
```

Résout l'équation `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), ou `adjoint(A) * X = B` (`trans = C`) en utilisant la factorisation `LU` calculée par `gttrf!`. `B` est écrasé avec la solution `X`.
