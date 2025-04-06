```
abspath(path::AbstractString, paths::AbstractString...) -> String
```

Convertir un ensemble de chemins en un chemin absolu en les joignant ensemble et en ajoutant le répertoire courant si nécessaire. Équivalent à `abspath(joinpath(path, paths...))`.
