```
link_pipe!(pipe; reader_supports_async=false, writer_supports_async=false)
```

Inicializa `pipe` y vincula el extremo `in` al extremo `out`. Los argumentos de palabra clave `reader_supports_async`/`writer_supports_async` corresponden a `OVERLAPPED` en Windows y `O_NONBLOCK` en sistemas POSIX. Deben ser `true` a menos que sean utilizados por un programa externo (por ejemplo, la salida de un comando ejecutado con [`run`](@ref)).
