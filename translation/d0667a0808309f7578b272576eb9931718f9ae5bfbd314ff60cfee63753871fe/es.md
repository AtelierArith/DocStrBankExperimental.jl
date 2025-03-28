```
trrfs!(uplo, trans, diag, A, B, X, Ferr, Berr) -> (Ferr, Berr)
```

Estima el error en la solución de `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), `adjoint(A) * X = B` (`trans = C`) para `side = L`, o las ecuaciones equivalentes de un `side = R` con `X * A` después de calcular `X` usando `trtrs!`. Si `uplo = U`, `A` es triangular superior. Si `uplo = L`, `A` es triangular inferior. Si `diag = N`, `A` tiene elementos diagonales no unitarios. Si `diag = U`, todos los elementos diagonales de `A` son uno. `Ferr` y `Berr` son entradas opcionales. `Ferr` es el error hacia adelante y `Berr` es el error hacia atrás, cada uno componente por componente.
