```
mkfifo(path::AbstractString, [mode::Integer]) -> path
```

Crea un archivo especial FIFO (un pipe con nombre) en `path`. Devuelve `path` tal como está en caso de éxito.

`mkfifo` solo es compatible con plataformas Unix.

!!! compat "Julia 1.11"
    `mkfifo` requiere al menos Julia 1.11.

