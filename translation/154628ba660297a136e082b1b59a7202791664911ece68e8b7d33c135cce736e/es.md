```
getrs!(trans, A, ipiv, B)
```

Resuelve la ecuación lineal `A * X = B`, `transpose(A) * X = B` o `adjoint(A) * X = B` para `A` cuadrada. Modifica la matriz/vector `B` en su lugar con la solución. `A` es la factorización `LU` de `getrf!`, con `ipiv` la información de pivoteo. `trans` puede ser uno de `N` (sin modificación), `T` (transpuesta) o `C` (transpuesta conjugada).
