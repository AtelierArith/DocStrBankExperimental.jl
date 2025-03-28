```
sytrf!(uplo, A, ipiv) -> (A, ipiv, info)
```

Berechnet die Bunch-Kaufman-Faktorisierung einer symmetrischen Matrix `A`. Wenn `uplo = U`, wird die obere Hälfte von `A` gespeichert. Wenn `uplo = L`, wird die untere Hälfte gespeichert.

Gibt `A` zurück, das durch die Faktorisierung überschrieben wird, den Pivot-Vektor `ipiv` und den Fehlercode `info`, der eine nicht-negative ganze Zahl ist. Wenn `info` positiv ist, ist die Matrix singulär und der diagonale Teil der Faktorisierung ist genau null an der Position `info`.
