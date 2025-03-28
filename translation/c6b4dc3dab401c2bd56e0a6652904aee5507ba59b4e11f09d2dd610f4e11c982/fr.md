```
gesdd!(job, A) -> (U, S, VT)
```

Trouve la décomposition en valeurs singulières de `A`, `A = U * S * V'`, en utilisant une approche de diviser pour régner. Si `job = A`, toutes les colonnes de `U` et les lignes de `V'` sont calculées. Si `job = N`, aucune colonne de `U` ou ligne de `V'` n'est calculée. Si `job = O`, `A` est écrasé avec les colonnes de (mince) `U` et les lignes de (mince) `V'`. Si `job = S`, les colonnes de (mince) `U` et les lignes de (mince) `V'` sont calculées et retournées séparément.
