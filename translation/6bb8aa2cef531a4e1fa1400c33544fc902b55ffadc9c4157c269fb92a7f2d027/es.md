```
ccall((nombre_función, biblioteca), tipo_retorno, (tipo_arg1, ...), valor_arg1, ...)
ccall(nombre_función, tipo_retorno, (tipo_arg1, ...), valor_arg1, ...)
ccall(puntero_función, tipo_retorno, (tipo_arg1, ...), valor_arg1, ...)
```

Llama a una función en una biblioteca compartida exportada en C, especificada por la tupla `(nombre_función, biblioteca)`, donde cada componente es una cadena o símbolo. En lugar de especificar una biblioteca, también se puede usar un símbolo o cadena `nombre_función`, que se resuelve en el proceso actual. Alternativamente, `ccall` también se puede usar para llamar a un puntero de función `puntero_función`, como el que devuelve `dlsym`.

Tenga en cuenta que la tupla de tipos de argumento debe ser una tupla literal, y no una variable o expresión de tipo tupla.

Cada `valor_arg` para el `ccall` se convertirá al correspondiente `tipo_arg`, mediante la inserción automática de llamadas a `unsafe_convert(tipo_arg, cconvert(tipo_arg, valor_arg))`. (Consulte también la documentación de [`unsafe_convert`](@ref Base.unsafe_convert) y [`cconvert`](@ref Base.cconvert) para más detalles). En la mayoría de los casos, esto simplemente resulta en una llamada a `convert(tipo_arg, valor_arg)`.
