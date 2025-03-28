```
stebz!(range, order, vl, vu, il, iu, abstol, dv, ev) -> (dv, iblock, isplit)
```

Berechnet die Eigenwerte für eine symmetrische tridiagonale Matrix mit `dv` als Diagonale und `ev` als Nebendiagonale. Wenn `range = A`, werden alle Eigenwerte gefunden. Wenn `range = V`, werden die Eigenwerte im halb-offenen Intervall `(vl, vu]` gefunden. Wenn `range = I`, werden die Eigenwerte mit Indizes zwischen `il` und `iu` gefunden. Wenn `order = B`, werden die Eigenwerte innerhalb eines Blocks geordnet. Wenn `order = E`, werden sie über alle Blöcke hinweg geordnet. `abstol` kann als Toleranz für die Konvergenz festgelegt werden.
