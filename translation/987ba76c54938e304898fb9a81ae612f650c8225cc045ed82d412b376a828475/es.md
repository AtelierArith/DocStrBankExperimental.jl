```
errormonitor(t::Task)
```

Imprime un registro de errores en `stderr` si la tarea `t` falla.

# Ejemplos

```julia-repl
julia> Base._wait(errormonitor(Threads.@spawn error("la tarea falló")))
Unhandled Task ERROR: la tarea falló
Stacktrace:
[...]
```
