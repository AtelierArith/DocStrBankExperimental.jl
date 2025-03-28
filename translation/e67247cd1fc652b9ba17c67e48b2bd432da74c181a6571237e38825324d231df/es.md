```
handle_message(logger, level, message, _module, group, id, file, line; key1=val1, ...)
```

Registra un mensaje en `logger` en el nivel `level`. La ubicación lógica en la que se generó el mensaje está dada por el módulo `_module` y el grupo; la ubicación de origen por `file` y `line`. `id` es un valor único arbitrario (típicamente un [`Symbol`](@ref)) que se utilizará como clave para identificar la declaración de registro al filtrar.
