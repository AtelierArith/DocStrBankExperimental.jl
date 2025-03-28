```
syev!(jobz, uplo, A)
```

Findet die Eigenwerte (`jobz = N`) oder Eigenwerte und Eigenvektoren (`jobz = V`) einer symmetrischen Matrix `A`. Wenn `uplo = U`, wird die obere Dreiecksmatrix von `A` verwendet. Wenn `uplo = L`, wird die untere Dreiecksmatrix von `A` verwendet.
