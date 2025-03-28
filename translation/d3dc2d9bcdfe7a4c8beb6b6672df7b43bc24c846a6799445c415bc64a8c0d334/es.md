```
readbytes!(stream::IOStream, b::AbstractVector{UInt8}, nb=length(b); all::Bool=true)
```

Lee como máximo `nb` bytes desde `stream` en `b`, devolviendo el número de bytes leídos. El tamaño de `b` se incrementará si es necesario (es decir, si `nb` es mayor que `length(b)` y se pudieron leer suficientes bytes), pero nunca se reducirá.

Si `all` es `true` (el valor predeterminado), esta función bloqueará repetidamente intentando leer todos los bytes solicitados, hasta que ocurra un error o se alcance el final del archivo. Si `all` es `false`, se realiza como máximo una llamada a `read`, y la cantidad de datos devueltos depende del dispositivo. Tenga en cuenta que no todos los tipos de flujo admiten la opción `all`.
