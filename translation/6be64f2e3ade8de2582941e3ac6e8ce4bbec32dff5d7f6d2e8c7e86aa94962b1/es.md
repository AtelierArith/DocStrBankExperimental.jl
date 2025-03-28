```
lstat(archivo)
```

Como [`stat`](@ref), pero para enlaces simbólicos obtiene la información del enlace en sí en lugar del archivo al que se refiere. Esta función debe ser llamada en una ruta de archivo en lugar de un objeto de archivo o un descriptor de archivo.
