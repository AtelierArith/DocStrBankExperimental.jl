```
pttrs!(D, E, B)
```

Löst `A * X = B` für positiv definit tridiagonal `A` mit Diagonale `D` und Nebendiagonale `E`, nachdem die LDLt-Faktorisierung von `A` mit `pttrf!` berechnet wurde. `B` wird mit der Lösung `X` überschrieben.
