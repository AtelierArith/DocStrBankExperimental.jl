```
bdsdc!(uplo, compq, d, e_) -> (d, e, u, vt, q, iq)
```

Berechnet die singuläre Wertzerlegung einer bidiagonalen Matrix mit `d` auf der Diagonalen und `e_` auf der Nebendiagonalen unter Verwendung einer Teile-und-herrsche-Methode. Wenn `uplo = U`, ist `e_` die Superdiagonale. Wenn `uplo = L`, ist `e_` die Subdiagonale. Wenn `compq = N`, werden nur die singulären Werte gefunden. Wenn `compq = I`, werden die singulären Werte und Vektoren gefunden. Wenn `compq = P`, werden die singulären Werte und Vektoren in kompakter Form gefunden. Funktioniert nur für reale Typen.

Gibt die singulären Werte in `d` zurück, und wenn `compq = P`, die kompakten singulären Vektoren in `iq`.
