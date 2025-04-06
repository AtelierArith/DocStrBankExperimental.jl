```
hesv!(uplo, A, B) -> (B, A, ipiv)
```

Findet die Lösung von `A * X = B` für die hermitische Matrix `A`. Wenn `uplo = U`, wird die obere Hälfte von `A` gespeichert. Wenn `uplo = L` ist, wird die untere Hälfte gespeichert. `B` wird durch die Lösung `X` überschrieben. `A` wird durch ihre Bunch-Kaufman-Faktorisierung überschrieben. `ipiv` enthält Pivotierungsinformationen über die Faktorisierung.
