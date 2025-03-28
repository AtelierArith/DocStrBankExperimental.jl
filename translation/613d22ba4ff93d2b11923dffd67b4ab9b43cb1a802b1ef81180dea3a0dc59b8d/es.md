```
GitConfig(path::AbstractString, level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP, force::Bool=false)
```

Crea un nuevo `GitConfig` cargando la información de configuración desde el archivo en `path`. Consulta [`addfile`](@ref) para más información sobre las opciones `level`, `repo` y `force`.
