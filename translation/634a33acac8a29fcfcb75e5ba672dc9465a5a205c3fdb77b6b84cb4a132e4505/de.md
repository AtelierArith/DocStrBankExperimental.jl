```
sygvd!(itype, jobz, uplo, A, B) -> (w, A, B)
```

Findet die verallgemeinerten Eigenwerte (`jobz = N`) oder Eigenwerte und Eigenvektoren (`jobz = V`) einer symmetrischen Matrix `A` und einer symmetrisch positiv definiten Matrix `B`. Wenn `uplo = U`, werden die oberen Dreiecke von `A` und `B` verwendet. Wenn `uplo = L`, werden die unteren Dreiecke von `A` und `B` verwendet. Wenn `itype = 1` ist, besteht das zu lösende Problem aus `A * x = lambda * B * x`. Wenn `itype = 2` ist, besteht das zu lösende Problem aus `A * B * x = lambda * x`. Wenn `itype = 3` ist, besteht das zu lösende Problem aus `B * A * x = lambda * x`.
