```
trtrs!(uplo, trans, diag, A, B)
```

Resuelve `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), o `adjoint(A) * X = B` (`trans = C`) para la matriz triangular `A` (superior si `uplo = U`, inferior si `uplo = L`). Si `diag = N`, `A` tiene elementos diagonales no unitarios. Si `diag = U`, todos los elementos diagonales de `A` son uno. `B` se sobrescribe con la solución `X`.
