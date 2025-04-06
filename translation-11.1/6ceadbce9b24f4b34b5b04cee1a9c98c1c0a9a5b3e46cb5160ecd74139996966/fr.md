```
gesvd!(jobu, jobvt, A) -> (U, S, VT)
```

Trouve la décomposition en valeurs singulières de `A`, `A = U * S * V'`. Si `jobu = A`, toutes les colonnes de `U` sont calculées. Si `jobvt = A`, toutes les lignes de `V'` sont calculées. Si `jobu = N`, aucune colonne de `U` n'est calculée. Si `jobvt = N`, aucune ligne de `V'` n'est calculée. Si `jobu = O`, `A` est écrasé avec les colonnes de (mince) `U`. Si `jobvt = O`, `A` est écrasé avec les lignes de (mince) `V'`. Si `jobu = S`, les colonnes de (mince) `U` sont calculées et retournées séparément. Si `jobvt = S`, les lignes de (mince) `V'` sont calculées et retournées séparément. `jobu` et `jobvt` ne peuvent pas être tous deux `O`.

Retourne `U`, `S`, et `Vt`, où `S` sont les valeurs singulières de `A`.
