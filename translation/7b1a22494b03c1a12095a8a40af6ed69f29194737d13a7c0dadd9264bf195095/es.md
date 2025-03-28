```
LogLevel(nivel)
```

Severidad/verbosidad de un registro de log.

El nivel de log proporciona una clave contra la cual se pueden filtrar los registros de log potenciales, antes de que se realice cualquier otro trabajo para construir la estructura de datos del registro de log en sí.

# Ejemplos

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
