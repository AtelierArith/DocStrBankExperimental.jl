```
hetrf!(uplo, A, ipiv) -> (A, ipiv, info)
```

Calcula la factorización de Bunch-Kaufman de una matriz hermitiana `A`. Si `uplo = U`, se almacena la mitad superior de `A`. Si `uplo = L`, se almacena la mitad inferior.

Devuelve `A`, sobrescrita por la factorización, el vector de pivote `ipiv`, y el código de error `info`, que es un entero no negativo. Si `info` es positivo, la matriz es singular y la parte diagonal de la factorización es exactamente cero en la posición `info`.
