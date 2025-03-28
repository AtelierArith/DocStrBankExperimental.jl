```
findmax!(rval, rind, A) -> (maxval, index)
```

Encuentra el máximo de `A` y el índice lineal correspondiente a lo largo de las dimensiones singleton de `rval` y `rind`, y almacena los resultados en `rval` y `rind`. `NaN` se trata como mayor que todos los demás valores excepto `missing`.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.

