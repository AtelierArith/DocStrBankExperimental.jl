```
getrf!(A) -> (A, ipiv, info)
```

Calcule la factorisation `LU` avec pivot de `A`, `A = LU`.

Renvoie `A`, modifié sur place, `ipiv`, les informations de pivotement, et un code `info` qui indique le succès (`info = 0`), une valeur singulière dans `U` (`info = i`, dans ce cas `U[i,i]` est singulier), ou un code d'erreur (`info < 0`).
