```
sytrs!(uplo, A, ipiv, B)
```

Resuelve la ecuación `A * X = B` para una matriz simétrica `A` utilizando los resultados de `sytrf!`. Si `uplo = U`, se almacena la mitad superior de `A`. Si `uplo = L`, se almacena la mitad inferior. `B` se sobrescribe con la solución `X`.
