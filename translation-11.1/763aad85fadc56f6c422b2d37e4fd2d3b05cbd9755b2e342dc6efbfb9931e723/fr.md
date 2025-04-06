```
bdsdc!(uplo, compq, d, e_) -> (d, e, u, vt, q, iq)
```

Calcule la décomposition en valeurs singulières d'une matrice bidiagonale avec `d` sur la diagonale et `e_` sur l'off-diagonale en utilisant une méthode de division et conquête. Si `uplo = U`, `e_` est la superdiagonale. Si `uplo = L`, `e_` est la sous-diagonale. Si `compq = N`, seules les valeurs singulières sont trouvées. Si `compq = I`, les valeurs et vecteurs singuliers sont trouvés. Si `compq = P`, les valeurs et vecteurs singuliers sont trouvés sous forme compacte. Fonctionne uniquement pour les types réels.

Renvoie les valeurs singulières dans `d`, et si `compq = P`, les vecteurs singuliers compacts dans `iq`.
