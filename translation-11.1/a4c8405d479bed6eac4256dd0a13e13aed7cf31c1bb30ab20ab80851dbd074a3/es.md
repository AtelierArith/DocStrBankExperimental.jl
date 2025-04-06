```
poll_fd(fd, timeout_s::Real=-1; readable=false, writable=false)
```

Monitorea un descriptor de archivo `fd` para cambios en la disponibilidad de lectura o escritura, y con un tiempo de espera dado por `timeout_s` segundos.

Los argumentos de palabra clave determinan cuál de los estados de lectura y/o escritura debe ser monitoreado; al menos uno de ellos debe estar configurado en `true`.

El valor devuelto es un objeto con campos booleanos `readable`, `writable` y `timedout`, que dan el resultado de la encuesta.
