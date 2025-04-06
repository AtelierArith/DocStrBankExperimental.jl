```
syevd!(jobz, uplo, A)
```

Findet die Eigenwerte (`jobz = N`) oder Eigenwerte und Eigenvektoren (`jobz = V`) einer symmetrischen Matrix `A`. Wenn `uplo = U`, wird die obere Dreiecksmatrix von `A` verwendet. Wenn `uplo = L`, wird die untere Dreiecksmatrix von `A` verwendet.

Verwendet die Divide-and-Conquer-Methode, anstelle der QR-Iteration, die von `syev!` verwendet wird, oder mehrere relativ robuste Darstellungen, die von `syevr!` verwendet werden. Siehe James W. Demmel et al, SIAM J. Sci. Comput. 30, 3, 1508 (2008) für einen Vergleich der Genauigkeit und Leistung verschiedener Methoden.
