```
getri!(A, ipiv)
```

Calcule l'inverse de `A`, en utilisant sa factorisation `LU` trouvée par `getrf!`. `ipiv` est l'information de pivot sortie et `A` contient la factorisation `LU` de `getrf!`. `A` est écrasé avec son inverse.
