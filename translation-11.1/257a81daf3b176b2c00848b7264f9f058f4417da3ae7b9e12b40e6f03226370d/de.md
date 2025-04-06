```
gttrs!(trans, dl, d, du, du2, ipiv, B)
```

Löst die Gleichung `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`) oder `adjoint(A) * X = B` (`trans = C`) unter Verwendung der `LU`-Faktorisierung, die mit `gttrf!` berechnet wurde. `B` wird mit der Lösung `X` überschrieben.
