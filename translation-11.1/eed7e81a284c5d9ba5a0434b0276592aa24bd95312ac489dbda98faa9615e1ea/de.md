```
sytri!(uplo, A, ipiv)
```

Berechnet die Inverse einer symmetrischen Matrix `A` unter Verwendung der Ergebnisse von `sytrf!`. Wenn `uplo = U`, wird die obere Hälfte von `A` gespeichert. Wenn `uplo = L`, wird die untere Hälfte gespeichert. `A` wird durch seine Inverse überschrieben.
