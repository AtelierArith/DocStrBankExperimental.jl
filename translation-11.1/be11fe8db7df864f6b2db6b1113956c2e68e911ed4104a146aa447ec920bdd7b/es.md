```
include_dependency(path::AbstractString; track_content::Bool=true)
```

En un módulo, declara que el archivo, directorio o enlace simbólico especificado por `path` (relativo o absoluto) es una dependencia para la precompilación; es decir, si `track_content=true`, el módulo necesitará ser recompilado si el contenido de `path` cambia (si `path` es un directorio, el contenido es igual a `join(readdir(path))`). Si `track_content=false`, la recompilación se activa cuando el tiempo de modificación `mtime` de `path` cambia.

Esto solo es necesario si tu módulo depende de una ruta que no se utiliza a través de [`include`](@ref). No tiene efecto fuera de la compilación.

!!! compat "Julia 1.11"
    El argumento clave `track_content` requiere al menos Julia 1.11. Ahora se lanza un error si `path` no es legible.

