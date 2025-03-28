```
sytrs!(uplo, A, ipiv, B)
```

Löst die Gleichung `A * X = B` für eine symmetrische Matrix `A` unter Verwendung der Ergebnisse von `sytrf!`. Wenn `uplo = U`, wird die obere Hälfte von `A` gespeichert. Wenn `uplo = L`, wird die untere Hälfte gespeichert. `B` wird durch die Lösung `X` überschrieben.
