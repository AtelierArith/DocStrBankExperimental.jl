```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

Lee como máximo `nb` bytes de `stream` en `b`, devolviendo el número de bytes leídos. El tamaño de `b` se incrementará si es necesario (es decir, si `nb` es mayor que `length(b)` y se pudieron leer suficientes bytes), pero nunca se reducirá.
