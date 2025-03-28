```
addfile(cfg::GitConfig, path::AbstractString,
        level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP,
        repo::Union{GitRepo, Nothing} = nothing,
        force::Bool=false)
```

Agrega un archivo de configuración de git existente ubicado en `path` a la configuración `GitConfig` actual `cfg`. Si el archivo no existe, se creará.

  * `level` establece el nivel de prioridad de la configuración de git y se determina por

[`Consts.GIT_CONFIG`](@ref).

  * `repo` es un repositorio opcional para permitir el análisis de inclusiones condicionales.
  * Si `force` es `false` y ya existe una configuración para el nivel de prioridad dado,

`addfile` generará un error. Si `force` es `true`, la configuración existente será reemplazada por la que se encuentra en el archivo en `path`.
