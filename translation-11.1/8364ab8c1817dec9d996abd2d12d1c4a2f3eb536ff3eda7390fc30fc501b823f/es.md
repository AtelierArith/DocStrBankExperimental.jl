```
fdio([name::AbstractString, ]fd::Integer[, own::Bool=false]) -> IOStream
```

Crea un objeto [`IOStream`](@ref) a partir de un descriptor de archivo entero. Si `own` es `true`, cerrar este objeto cerrará el descriptor subyacente. Por defecto, un `IOStream` se cierra cuando es recolectado por el recolector de basura. `name` te permite asociar el descriptor con un archivo nombrado.
