```
@test_warn msg expr
```

Prueba si la evaluación de `expr` resulta en una salida de [`stderr`](@ref) que contenga la cadena `msg` o coincida con la expresión regular `msg`. Si `msg` es una función booleana, prueba si `msg(output)` devuelve `true`. Si `msg` es una tupla o un arreglo, verifica que la salida de error contenga/coincida con cada elemento en `msg`. Devuelve el resultado de evaluar `expr`.

Consulta también [`@test_nowarn`](@ref) para verificar la ausencia de salida de error.

Nota: Las advertencias generadas por `@warn` no se pueden probar con esta macro. Usa [`@test_logs`](@ref) en su lugar.
