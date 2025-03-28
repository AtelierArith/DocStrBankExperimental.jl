```
GeneralizedSchur <: Factorization
```

Tipo de factorización de matriz de la factorización de Schur generalizada de dos matrices `A` y `B`. Este es el tipo de retorno de [`schur(_, _)`](@ref), la función de factorización de matriz correspondiente.

Si `F::GeneralizedSchur` es el objeto de factorización, los factores de Schur (cuasi) triangulares se pueden obtener a través de `F.S` y `F.T`, los vectores de Schur unitarios/ortogonales a la izquierda a través de `F.left` o `F.Q`, y los vectores de Schur unitarios/ortogonales a la derecha se pueden obtener con `F.right` o `F.Z` de tal manera que `A=F.left*F.S*F.right'` y `B=F.left*F.T*F.right'`. Los valores propios generalizados de `A` y `B` se pueden obtener con `F.α./F.β`.

Iterar la descomposición produce los componentes `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` y `F.β`.
