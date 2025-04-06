```
trrfs!(uplo, trans, diag, A, B, X, Ferr, Berr) -> (Ferr, Berr)
```

Schätzt den Fehler in der Lösung von `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), `adjoint(A) * X = B` (`trans = C`) für `side = L`, oder die äquivalenten Gleichungen für eine rechtsseitige `side = R` `X * A`, nachdem `X` mit `trtrs!` berechnet wurde. Wenn `uplo = U`, ist `A` oberhalb triangulär. Wenn `uplo = L`, ist `A` unterhalb triangulär. Wenn `diag = N`, hat `A` nicht-einheitliche Diagonalelemente. Wenn `diag = U`, sind alle Diagonalelemente von `A` eins. `Ferr` und `Berr` sind optionale Eingaben. `Ferr` ist der Vorwärtsfehler und `Berr` ist der Rückwärtsfehler, jeweils komponentenweise.
