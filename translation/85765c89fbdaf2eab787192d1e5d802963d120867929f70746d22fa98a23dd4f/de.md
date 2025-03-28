```
trtrs!(uplo, trans, diag, A, B)
```

Löst `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`) oder `adjoint(A) * X = B` (`trans = C`) für die (obere, wenn `uplo = U`, untere, wenn `uplo = L`) dreieckige Matrix `A`. Wenn `diag = N`, hat `A` nicht-einheitliche Diagonalelemente. Wenn `diag = U`, sind alle Diagonalelemente von `A` eins. `B` wird mit der Lösung `X` überschrieben.
