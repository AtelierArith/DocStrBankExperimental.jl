```
@test_nowarn expr
```

Prueba si la evaluación de `expr` resulta en una salida vacía de [`stderr`](@ref) (sin advertencias ni otros mensajes). Devuelve el resultado de evaluar `expr`.

Nota: La ausencia de advertencias generadas por `@warn` no se puede probar con este macro. Usa [`@test_logs`](@ref) en su lugar.
