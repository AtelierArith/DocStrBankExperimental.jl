```
addfile(cfg::GitConfig, path::AbstractString,
        level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP,
        repo::Union{GitRepo, Nothing} = nothing,
        force::Bool=false)
```

Fügen Sie eine vorhandene Git-Konfigurationsdatei, die sich unter `path` befindet, zur aktuellen `GitConfig` `cfg` hinzu. Wenn die Datei nicht existiert, wird sie erstellt.

  * `level` legt die Prioritätsstufe der Git-Konfiguration fest und wird durch

[`Consts.GIT_CONFIG`](@ref) bestimmt.

  * `repo` ist ein optionales Repository, um das Parsen von bedingten Includes zu ermöglichen.
  * Wenn `force` `false` ist und eine Konfiguration für die gegebene Prioritätsstufe bereits existiert,

wird `addfile` einen Fehler auslösen. Wenn `force` `true` ist, wird die vorhandene Konfiguration durch die im Datei unter `path` ersetzt.
