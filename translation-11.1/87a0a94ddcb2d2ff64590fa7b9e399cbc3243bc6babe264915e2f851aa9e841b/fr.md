```
gttrf!(dl, d, du) -> (dl, d, du, du2, ipiv)
```

Trouve la factorisation `LU` d'une matrice tridiagonale avec `dl` sur la sous-diagonale, `d` sur la diagonale, et `du` sur la superdiagonale.

Modifie `dl`, `d`, et `du` sur place et les retourne ainsi que la deuxième superdiagonale `du2` et le vecteur de pivotage `ipiv`.
