```
bdsqr!(uplo, d, e_, Vt, U, C) -> (d, Vt, U, C)
```

Berechnet die singuläre Wertzerlegung einer bidiagonalen Matrix mit `d` auf der Diagonalen und `e_` auf der Nebendiagonalen. Wenn `uplo = U`, ist `e_` die Superdiagonale. Wenn `uplo = L`, ist `e_` die Subdiagonale. Kann optional auch das Produkt `Q' * C` berechnen.

Gibt die singulären Werte in `d` zurück, und die Matrix `C` wird mit `Q' * C` überschrieben.
