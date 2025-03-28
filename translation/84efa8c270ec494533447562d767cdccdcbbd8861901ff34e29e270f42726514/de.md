```
ggev3!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

Findet die verallgemeinerte Eigenzerlegung von `A` und `B` unter Verwendung eines blockierten Algorithmus. Wenn `jobvl = N`, werden die linken Eigenvektoren nicht berechnet. Wenn `jobvr = N`, werden die rechten Eigenvektoren nicht berechnet. Wenn `jobvl = V` oder `jobvr = V`, werden die entsprechenden Eigenvektoren berechnet. Diese Funktion erfordert LAPACK 3.6.0.
