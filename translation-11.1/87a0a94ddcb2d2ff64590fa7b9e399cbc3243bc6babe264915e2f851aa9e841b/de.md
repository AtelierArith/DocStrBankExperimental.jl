```
gttrf!(dl, d, du) -> (dl, d, du, du2, ipiv)
```

Findet die `LU`-Faktorisierung einer tridiagonalen Matrix mit `dl` auf der Subdiagonale, `d` auf der Diagonale und `du` auf der Superdiagonale.

Modifiziert `dl`, `d` und `du` in-place und gibt sie sowie die zweite Superdiagonale `du2` und den Pivot-Vektor `ipiv` zurück.
