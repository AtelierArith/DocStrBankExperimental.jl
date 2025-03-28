```
gesdd!(job, A) -> (U, S, VT)
```

Encuentra la descomposición en valores singulares de `A`, `A = U * S * V'`, utilizando un enfoque de dividir y conquistar. Si `job = A`, se computan todas las columnas de `U` y las filas de `V'`. Si `job = N`, no se computan columnas de `U` ni filas de `V'`. Si `job = O`, `A` se sobrescribe con las columnas de (delgadas) `U` y las filas de (delgadas) `V'`. Si `job = S`, se computan y devuelven por separado las columnas de (delgadas) `U` y las filas de (delgadas) `V'`.
