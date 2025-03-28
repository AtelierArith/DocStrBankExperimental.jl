```
gesv!(A, B) -> (B, A, ipiv)
```

Resuelve la ecuación lineal `A * X = B` donde `A` es una matriz cuadrada utilizando la factorización `LU` de `A`. `A` se sobrescribe con su factorización `LU` y `B` se sobrescribe con la solución `X`. `ipiv` contiene la información de pivoteo para la factorización `LU` de `A`.
