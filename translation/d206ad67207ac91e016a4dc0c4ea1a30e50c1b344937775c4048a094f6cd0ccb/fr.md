```
getrf!(A, ipiv) -> (A, ipiv, info)
```

Calculez la factorisation `LU` pivotée de `A`, `A = LU`. `ipiv` contient les informations de pivotement et `info` un code qui indique le succès (`info = 0`), une valeur singulière dans `U` (`info = i`, dans ce cas `U[i,i]` est singulier), ou un code d'erreur (`info < 0`).
