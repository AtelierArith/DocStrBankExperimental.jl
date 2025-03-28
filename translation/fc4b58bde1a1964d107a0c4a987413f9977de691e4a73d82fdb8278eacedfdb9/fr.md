```
ZeroPivotException <: Exception
```

Exception levée lorsqu'une factorisation/résolution de matrice rencontre un zéro dans une position de pivot (diagonale) et ne peut pas continuer. Cela ne signifie *pas* que la matrice est singulière : il peut être utile de passer à une autre factorisation telle que LU avec pivot qui peut réorganiser les variables pour éliminer les pivots nuls spuriques. Le champ `info` indique l'emplacement de (l'un des) pivots nuls.
