```
chmod(path::AbstractString, mode::Integer; recursive::Bool=false)
```

Cambia el modo de permisos de `path` a `mode`. Actualmente, solo se admiten modos `mode` enteros (por ejemplo, `0o777`). Si `recursive=true` y la ruta es un directorio, todos los permisos en ese directorio se cambiarán recursivamente. Devuelve `path`.

!!! nota
    Antes de Julia 1.6, esto no manipulaba correctamente los ACL del sistema de archivos en Windows, por lo que solo establecía bits de solo lectura en los archivos. Ahora puede manipular los ACL.

