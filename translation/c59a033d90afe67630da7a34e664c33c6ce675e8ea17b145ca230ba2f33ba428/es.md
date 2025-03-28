```
schur(A, B) -> F::GeneralizedSchur
```

Calcula la factorización Schur generalizada (o QZ) de las matrices `A` y `B`. Los factores Schur (cuasi) triangulares se pueden obtener del objeto `Schur` `F` con `F.S` y `F.T`, los vectores Schur unitarios/ortogonales izquierdos se pueden obtener con `F.left` o `F.Q` y los vectores Schur unitarios/ortogonales derechos se pueden obtener con `F.right` o `F.Z` de tal manera que `A=F.left*F.S*F.right'` y `B=F.left*F.T*F.right'`. Los valores propios generalizados de `A` y `B` se pueden obtener con `F.α./F.β`.

Iterar la descomposición produce los componentes `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` y `F.β`.
