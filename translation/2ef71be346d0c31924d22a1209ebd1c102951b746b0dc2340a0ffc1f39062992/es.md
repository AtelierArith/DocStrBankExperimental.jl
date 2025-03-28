```
realpath(path::AbstractString) -> String
```

Canonicaliza una ruta expandiendo enlaces simbólicos y eliminando entradas "." y "..". En sistemas de archivos que son insensibles a mayúsculas y conservan el caso (típicamente Mac y Windows), se devuelve el caso almacenado por el sistema de archivos para la ruta.

(Esta función lanza una excepción si `path` no existe en el sistema de archivos.)
