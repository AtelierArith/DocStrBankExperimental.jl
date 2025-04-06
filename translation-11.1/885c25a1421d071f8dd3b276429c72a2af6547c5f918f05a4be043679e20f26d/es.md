```
normpath(path::AbstractString, paths::AbstractString...) -> String
```

Convierte un conjunto de rutas a una ruta normalizada al unirlas y eliminar las entradas "." y "..". Equivalente a `normpath(joinpath(path, paths...))`.
