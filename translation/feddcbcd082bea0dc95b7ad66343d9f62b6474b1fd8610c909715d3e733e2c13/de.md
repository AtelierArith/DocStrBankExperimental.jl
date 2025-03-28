```
syconv!(uplo, A, ipiv) -> (A, work)
```

Konvertiert eine symmetrische Matrix `A` (die in eine dreieckige Matrix faktorisiert wurde) in zwei Matrizen `L` und `D`. Wenn `uplo = U`, ist `A` oberhalb dreieckig. Wenn `uplo = L`, ist sie unterhalb dreieckig. `ipiv` ist der Pivotvektor aus der dreieckigen Faktorisierung. `A` wird durch `L` und `D` überschrieben.
