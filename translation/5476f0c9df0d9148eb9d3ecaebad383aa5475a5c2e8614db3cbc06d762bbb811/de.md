```
syevr!(jobz, range, uplo, A, vl, vu, il, iu, abstol) -> (W, Z)
```

Findet die Eigenwerte (`jobz = N`) oder Eigenwerte und Eigenvektoren (`jobz = V`) einer symmetrischen Matrix `A`. Wenn `uplo = U`, wird die obere Dreiecksmatrix von `A` verwendet. Wenn `uplo = L`, wird die untere Dreiecksmatrix von `A` verwendet. Wenn `range = A`, werden alle Eigenwerte gefunden. Wenn `range = V`, werden die Eigenwerte im halb-offenen Intervall `(vl, vu]` gefunden. Wenn `range = I`, werden die Eigenwerte mit Indizes zwischen `il` und `iu` gefunden. `abstol` kann als Toleranz für die Konvergenz festgelegt werden.

Die Eigenwerte werden in `W` und die Eigenvektoren in `Z` zurückgegeben.
