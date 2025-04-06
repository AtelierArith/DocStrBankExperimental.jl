```
ormqr!(seite, trans, A, tau, C)
```

Berechnet `Q * C` (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`) für `seite = L` oder die äquivalente rechtsseitige Multiplikation für `seite = R` unter Verwendung von `Q` aus einer `QR`-Faktorisierung von `A`, die mit `geqrf!` berechnet wurde. `C` wird überschrieben.
