```
hesv!(uplo, A, B) -> (B, A, ipiv)
```

Encuentra la solución a `A * X = B` para la matriz hermítica `A`. Si `uplo = U`, se almacena la mitad superior de `A`. Si `uplo = L`, se almacena la mitad inferior. `B` se sobrescribe con la solución `X`. `A` se sobrescribe con su factorización de Bunch-Kaufman. `ipiv` contiene información de pivoteo sobre la factorización.
