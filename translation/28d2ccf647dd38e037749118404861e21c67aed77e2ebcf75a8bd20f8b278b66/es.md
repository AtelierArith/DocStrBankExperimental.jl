```
abspath(path::AbstractString, paths::AbstractString...) -> String
```

Convierte un conjunto de rutas a una ruta absoluta al unirlas y agregar el directorio actual si es necesario. Equivalente a `abspath(joinpath(path, paths...))`.
