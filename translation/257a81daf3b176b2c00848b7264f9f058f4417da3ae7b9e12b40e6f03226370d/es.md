```
gttrs!(trans, dl, d, du, du2, ipiv, B)
```

Resuelve la ecuación `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), o `adjoint(A) * X = B` (`trans = C`) utilizando la factorización `LU` calculada por `gttrf!`. `B` se sobrescribe con la solución `X`.
