```
geqp3!(A, [jpvt, tau]) -> (A, tau, jpvt)
```

Calcula la factorización `QR` con pivoteo de `A`, `AP = QR` utilizando BLAS de nivel 3. `P` es una matriz de pivoteo, representada por `jpvt`. `tau` almacena los reflectores elementales. Los argumentos `jpvt` y `tau` son opcionales y permiten pasar arreglos preasignados. Cuando se pasan, `jpvt` debe tener una longitud mayor o igual a `n` si `A` es una matriz de `(m x n)` y `tau` debe tener una longitud mayor o igual a la dimensión más pequeña de `A`. Al entrar, si `jpvt[j]` no es igual a cero, entonces la columna `j` de `A` se permuta al frente de `AP`.

`A`, `jpvt` y `tau` se modifican en su lugar.
