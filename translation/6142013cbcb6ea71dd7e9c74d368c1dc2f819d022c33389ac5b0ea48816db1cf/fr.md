```
bdsqr!(uplo, d, e_, Vt, U, C) -> (d, Vt, U, C)
```

Calcule la décomposition en valeurs singulières d'une matrice bidiagonale avec `d` sur la diagonale et `e_` sur l'off-diagonale. Si `uplo = U`, `e_` est la superdiagonale. Si `uplo = L`, `e_` est la sous-diagonale. Peut également calculer en option le produit `Q' * C`.

Renvoie les valeurs singulières dans `d`, et la matrice `C` écrasée avec `Q' * C`.
