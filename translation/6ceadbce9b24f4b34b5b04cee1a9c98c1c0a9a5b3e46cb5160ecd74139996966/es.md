```
gesvd!(jobu, jobvt, A) -> (U, S, VT)
```

Encuentra la descomposición en valores singulares de `A`, `A = U * S * V'`. Si `jobu = A`, se computan todas las columnas de `U`. Si `jobvt = A`, se computan todas las filas de `V'`. Si `jobu = N`, no se computan columnas de `U`. Si `jobvt = N`, no se computan filas de `V'`. Si `jobu = O`, `A` se sobrescribe con las columnas de (delgada) `U`. Si `jobvt = O`, `A` se sobrescribe con las filas de (delgada) `V'`. Si `jobu = S`, se computan y devuelven por separado las columnas de (delgada) `U`. Si `jobvt = S`, se computan y devuelven por separado las filas de (delgada) `V'`. `jobu` y `jobvt` no pueden ser ambos `O`.

Devuelve `U`, `S` y `Vt`, donde `S` son los valores singulares de `A`.
