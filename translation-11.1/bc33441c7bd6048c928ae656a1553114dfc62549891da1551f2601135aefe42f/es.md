```
homedir() -> String
```

Devuelve el directorio home del usuario actual.

!!! note
    `homedir` determina el directorio home a través de `libuv`'s `uv_os_homedir`. Para más detalles (por ejemplo, sobre cómo especificar el directorio home a través de variables de entorno), consulta la [documentación de `uv_os_homedir`](http://docs.libuv.org/en/v1.x/misc.html#c.uv_os_homedir).


Consulta también [`Sys.username`](@ref).
