```
pstrf!(uplo, A, tol) -> (A, piv, rank, info)
```

Calcula la descomposición de Cholesky con pivoteo (superior si `uplo = U`, inferior si `uplo = L`) de la matriz definida positiva `A` con una tolerancia establecida por el usuario `tol`. `A` se sobrescribe con su descomposición de Cholesky.

Devuelve `A`, los pivotes `piv`, el rango de `A` y un código `info`. Si `info = 0`, la factorización tuvo éxito. Si `info = i > 0`, entonces `A` es indefinida o deficiente en rango.
