```
normpath(path::AbstractString, paths::AbstractString...) -> String
```

Convertir un ensemble de chemins en un chemin normalisé en les joignant ensemble et en supprimant les entrées "." et "..". Équivalent à `normpath(joinpath(path, paths...))`.
