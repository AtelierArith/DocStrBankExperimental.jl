```
geqp3!(A, [jpvt, tau]) -> (A, tau, jpvt)
```

Berechnen Sie die pivotierte `QR`-Faktorisierung von `A`, `AP = QR` unter Verwendung von BLAS der Stufe 3. `P` ist eine Pivotmatrix, die durch `jpvt` dargestellt wird. `tau` speichert die elementaren Reflektoren. Die Argumente `jpvt` und `tau` sind optional und ermöglichen das Übergeben von vorallocierten Arrays. Wenn sie übergeben werden, muss `jpvt` eine Länge haben, die größer oder gleich `n` ist, wenn `A` eine `(m x n)`-Matrix ist, und `tau` muss eine Länge haben, die größer oder gleich der kleineren Dimension von `A` ist. Bei Eingabe, wenn `jpvt[j]` ungleich null ist, wird die `j`-te Spalte von `A` an den Anfang von `AP` permutiert.

`A`, `jpvt` und `tau` werden in-place modifiziert.
