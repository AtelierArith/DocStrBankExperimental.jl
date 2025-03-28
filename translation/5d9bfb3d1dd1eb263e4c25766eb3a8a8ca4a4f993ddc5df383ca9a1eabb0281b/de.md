```
stegr!(jobz, range, dv, ev, vl, vu, il, iu) -> (w, Z)
```

Berechnet die Eigenwerte (`jobz = N`) oder Eigenwerte und Eigenvektoren (`jobz = V`) für eine symmetrische tridiagonale Matrix mit `dv` als Diagonale und `ev` als Nebendiagonale. Wenn `range = A`, werden alle Eigenwerte gefunden. Wenn `range = V`, werden die Eigenwerte im halb-offenen Intervall `(vl, vu]` gefunden. Wenn `range = I`, werden die Eigenwerte mit Indizes zwischen `il` und `iu` gefunden. Die Eigenwerte werden in `w` und die Eigenvektoren in `Z` zurückgegeben.
