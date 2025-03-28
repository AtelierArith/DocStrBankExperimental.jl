```
GitConfig(path::AbstractString, level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP, force::Bool=false)
```

Créez un nouveau `GitConfig` en chargeant les informations de configuration à partir du fichier à `path`. Voir [`addfile`](@ref) pour plus d'informations sur les options `level`, `repo` et `force`.
