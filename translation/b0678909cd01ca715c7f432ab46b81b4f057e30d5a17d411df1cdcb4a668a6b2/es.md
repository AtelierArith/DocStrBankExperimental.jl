```
gecon!(normtype, A, anorm)
```

Encuentra el número de condición recíproco de la matriz `A`. Si `normtype = I`, el número de condición se encuentra en la norma infinita. Si `normtype = O` o `1`, el número de condición se encuentra en la norma uno. `A` debe ser el resultado de `getrf!` y `anorm` es la norma de `A` en la norma relevante.
