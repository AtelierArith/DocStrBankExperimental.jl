```
stein!(dv, ev_in, w_in, iblock_in, isplit_in)
```

Calcule les vecteurs propres pour une matrice tridiagonale symétrique avec `dv` comme diagonale et `ev_in` comme hors-diagonale. `w_in` spécifie les valeurs propres d'entrée pour lesquelles trouver les vecteurs propres correspondants. `iblock_in` spécifie les sous-matrices correspondant aux valeurs propres dans `w_in`. `isplit_in` spécifie les points de séparation entre les blocs de sous-matrices.
