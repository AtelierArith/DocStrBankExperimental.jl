```
trcon!(norm, uplo, diag, A)
```

Encuentra el número de condición recíproco de la matriz triangular `A` (superior si `uplo = U`, inferior si `uplo = L`). Si `diag = N`, `A` tiene elementos diagonales no unitarios. Si `diag = U`, todos los elementos diagonales de `A` son uno. Si `norm = I`, el número de condición se encuentra en la norma infinita. Si `norm = O` o `1`, el número de condición se encuentra en la norma uno.
