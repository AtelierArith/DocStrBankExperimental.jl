```
ordschur(F::GeneralizedSchur, select::Union{Vector{Bool},BitVector}) -> F::GeneralizedSchur
```

Reordena la factorización de Schur generalizada `F` de un par de matrices `(A, B) = (Q*S*Z', Q*T*Z')` de acuerdo con el arreglo lógico `select` y devuelve un objeto GeneralizedSchur `F`. Los valores propios seleccionados aparecen en la diagonal principal de ambos `F.S` y `F.T`, y los vectores de Schur ortogonales/unitarios izquierdo y derecho también se reordenan de tal manera que `(A, B) = F.Q*(F.S, F.T)*F.Z'` aún se mantiene y los valores propios generalizados de `A` y `B` aún se pueden obtener con `F.α./F.β`.
