```
unsafe_copyto!(dest::Ptr{T}, src::Ptr{T}, N)
```

Copia `N` elementos de un puntero de origen a un destino, sin ninguna verificación. El tamaño de un elemento se determina por el tipo de los punteros.

El prefijo `unsafe` en esta función indica que no se realiza ninguna validación en los punteros `dest` y `src` para asegurar que sean válidos. Un uso incorrecto puede corromper o causar un fallo de segmentación en tu programa, de la misma manera que en C.
