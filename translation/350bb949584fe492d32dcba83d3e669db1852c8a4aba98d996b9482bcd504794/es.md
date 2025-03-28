```
watch_folder(path::AbstractString, timeout_s::Real=-1)
```

Observa un archivo o directorio `path` en busca de cambios hasta que ocurra un cambio o transcurran `timeout_s` segundos. Esta función no sondea el sistema de archivos y, en su lugar, utiliza funcionalidades específicas de la plataforma para recibir notificaciones del sistema operativo (por ejemplo, a través de inotify en Linux). Consulte la documentación de NodeJS vinculada a continuación para obtener más detalles.

Esto continuará rastreando cambios para `path` en segundo plano hasta que se llame a `unwatch_folder` en el mismo `path`.

El valor devuelto es un par donde el primer campo es el nombre del archivo cambiado (si está disponible) y el segundo campo es un objeto con campos booleanos `renamed`, `changed` y `timedout`, que indican el evento.

Este comportamiento de esta función varía ligeramente entre plataformas. Consulte [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) para obtener información más detallada.
