```
trsen!(trabajo, compq, seleccionar, T, Q) -> (T, Q, w, s, sep)
trsen!(seleccionar, T, Q) -> (T, Q, w, s, sep)
```

Reordena la factorización de Schur de una matriz y opcionalmente encuentra números de condición recíprocos. Si `trabajo = N`, no se encuentran números de condición. Si `trabajo = E`, solo se encuentra el número de condición para este clúster de valores propios. Si `trabajo = V`, solo se encuentra el número de condición para el subespacio invariante. Si `trabajo = B`, entonces se encuentran los números de condición para el clúster y el subespacio. Si `compq = V`, los vectores de Schur `Q` se actualizan. Si `compq = N`, los vectores de Schur no se modifican. `seleccionar` determina qué valores propios están en el clúster. El método de 3 argumentos llama al método de 5 argumentos con `trabajo = N` y `compq = V`.

Devuelve `T`, `Q`, valores propios reordenados en `w`, el número de condición del clúster de valores propios `s`, y el número de condición del subespacio invariante `sep`.
