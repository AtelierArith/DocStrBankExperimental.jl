```
SimpleLogger([stream,] min_level=Info)
```

Registrador simplista para registrar todos los mensajes con un nivel mayor o igual a `min_level` en `stream`. Si el stream está cerrado, entonces los mensajes con un nivel de registro mayor o igual a `Warn` se registrarán en `stderr` y los inferiores en `stdout`.
