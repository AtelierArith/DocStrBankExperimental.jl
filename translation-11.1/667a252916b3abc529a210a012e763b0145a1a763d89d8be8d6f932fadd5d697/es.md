```
disable_logging(level)
```

Desactiva todos los mensajes de registro en niveles de registro iguales o inferiores a `level`. Esta es una configuración *global*, destinada a hacer que el registro de depuración sea extremadamente barato cuando está desactivado.

# Ejemplos

```julia
Logging.disable_logging(Logging.Info) # Desactivar depuración e información
```
