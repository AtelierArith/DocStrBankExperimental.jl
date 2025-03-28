```
sytrf!(uplo, A, ipiv) -> (A, ipiv, info)
```

Calcula la factorización de Bunch-Kaufman de una matriz simétrica `A`. Si `uplo = U`, la mitad superior de `A` se almacena. Si `uplo = L`, la mitad inferior se almacena.

Devuelve `A`, sobrescrita por la factorización, el vector de pivote `ipiv`, y el código de error `info` que es un entero no negativo. Si `info` es positivo, la matriz es singular y la parte diagonal de la factorización es exactamente cero en la posición `info`.
