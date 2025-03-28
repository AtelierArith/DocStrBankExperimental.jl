```
sysv!(uplo, A, B) -> (B, A, ipiv)
```

Encuentra la solución a `A * X = B` para la matriz simétrica `A`. Si `uplo = U`, la mitad superior de `A` se almacena. Si `uplo = L`, la mitad inferior se almacena. `B` se sobrescribe con la solución `X`. `A` se sobrescribe con su factorización de Bunch-Kaufman. `ipiv` contiene información de pivoteo sobre la factorización.
