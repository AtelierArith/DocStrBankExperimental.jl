```
gebak!(job, side, ilo, ihi, scale, V)
```

Transformez les vecteurs propres `V` d'une matrice équilibrée à l'aide de `gebal!` en les vecteurs propres non mis à l'échelle/non permutés de la matrice d'origine. Modifie `V` sur place. `side` peut être `L` (les vecteurs propres à gauche sont transformés) ou `R` (les vecteurs propres à droite sont transformés).
