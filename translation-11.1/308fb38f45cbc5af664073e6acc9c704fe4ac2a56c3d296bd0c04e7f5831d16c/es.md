```
unsafe_string(p::Ptr{UInt8}, [length::Integer])
```

Copia una cadena desde la dirección de una cadena al estilo C (terminada en NUL) codificada como UTF-8. (El puntero se puede liberar de forma segura después). Si se especifica `length` (la longitud de los datos en bytes), la cadena no tiene que estar terminada en NUL.

Esta función está etiquetada como "insegura" porque se bloqueará si `p` no es una dirección de memoria válida para los datos de la longitud solicitada.
