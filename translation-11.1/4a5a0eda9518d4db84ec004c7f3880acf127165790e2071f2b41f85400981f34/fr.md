```
RankDeficientException
```

Exception levée lorsque la matrice d'entrée est [déficiente en rang](https://en.wikipedia.org/wiki/Rank_(linear_algebra)). Certaines fonctions d'algèbre linéaire, telles que la décomposition de Cholesky, ne s'appliquent qu'aux matrices qui ne sont pas déficientes en rang. Le champ `info` indique le rang calculé de la matrice.
