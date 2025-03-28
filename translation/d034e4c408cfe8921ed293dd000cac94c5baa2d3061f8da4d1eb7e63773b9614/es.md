```
watch_file(path::AbstractString, timeout_s::Real=-1)
```

Observa el archivo o directorio `path` en busca de cambios hasta que ocurra un cambio o transcurran `timeout_s` segundos. Esta función no sondea el sistema de archivos y, en su lugar, utiliza funcionalidades específicas de la plataforma para recibir notificaciones del sistema operativo (por ejemplo, a través de inotify en Linux). Consulta la documentación de NodeJS vinculada a continuación para más detalles.

El valor devuelto es un objeto con campos booleanos `renamed`, `changed` y `timedout`, que indican el resultado de la observación del archivo.

Este comportamiento de esta función varía ligeramente entre plataformas. Consulta [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) para obtener información más detallada.
