```
sysv!(uplo, A, B) -> (B, A, ipiv)
```

Findet die Lösung für `A * X = B` für die symmetrische Matrix `A`. Wenn `uplo = U`, wird die obere Hälfte von `A` gespeichert. Wenn `uplo = L`, wird die untere Hälfte gespeichert. `B` wird durch die Lösung `X` überschrieben. `A` wird durch ihre Bunch-Kaufman-Faktorisierung überschrieben. `ipiv` enthält Pivotierungsinformationen über die Faktorisierung.
