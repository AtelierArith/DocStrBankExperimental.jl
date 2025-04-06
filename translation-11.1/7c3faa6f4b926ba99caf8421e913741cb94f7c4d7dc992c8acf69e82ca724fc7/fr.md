```
addfile(cfg::GitConfig, path::AbstractString,
        level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP,
        repo::Union{GitRepo, Nothing} = nothing,
        force::Bool=false)
```

Ajoute un fichier de configuration git existant situé à `path` à la configuration `GitConfig` actuelle `cfg`. Si le fichier n'existe pas, il sera créé.

  * `level` définit le niveau de priorité de la configuration git et est déterminé par

[`Consts.GIT_CONFIG`](@ref).

  * `repo` est un dépôt optionnel pour permettre l'analyse des inclusions conditionnelles.
  * Si `force` est `false` et qu'une configuration pour le niveau de priorité donné existe déjà,

`addfile` renverra une erreur. Si `force` est `true`, la configuration existante sera remplacée par celle du fichier à `path`.
