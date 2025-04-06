```
read(s::IOStream, nb::Integer; all=true)
```

Lee como máximo `nb` bytes de `s`, devolviendo un `Vector{UInt8}` de los bytes leídos.

Si `all` es `true` (el valor predeterminado), esta función bloqueará repetidamente intentando leer todos los bytes solicitados, hasta que ocurra un error o se alcance el final del archivo. Si `all` es `false`, se realiza como máximo una llamada a `read`, y la cantidad de datos devueltos depende del dispositivo. Ten en cuenta que no todos los tipos de flujo admiten la opción `all`.
