```
gebrd!(A) -> (A, d, e, tauq, taup)
```

Réduit `A` sur place à la forme bidiagonale `A = QBP'`. Renvoie `A`, contenant la matrice bidiagonale `B`; `d`, contenant les éléments diagonaux de `B`; `e`, contenant les éléments hors-diagonaux de `B`; `tauq`, contenant les réflecteurs élémentaires représentant `Q`; et `taup`, contenant les réflecteurs élémentaires représentant `P`.
