```
LibGit2.init(path::AbstractString, bare::Bool=false) -> GitRepo
```

Abre un nuevo repositorio git en `path`. Si `bare` es `false`, el árbol de trabajo se creará en `path/.git`. Si `bare` es `true`, no se creará ningún directorio de trabajo.
