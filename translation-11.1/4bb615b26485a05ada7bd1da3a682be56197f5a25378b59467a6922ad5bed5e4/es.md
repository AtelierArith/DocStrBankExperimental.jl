```
unwatch_folder(path::AbstractString)
```

Detener el seguimiento en segundo plano de los cambios para `path`. No se recomienda hacer esto mientras otra tarea está esperando que `watch_folder` devuelva en la misma ruta, ya que el resultado puede ser impredecible.
