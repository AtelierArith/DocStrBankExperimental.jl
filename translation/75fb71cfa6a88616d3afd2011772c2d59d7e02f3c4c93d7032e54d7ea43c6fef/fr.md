```
select_downloadable_artifacts(artifacts_toml::String;
                              platform = HostPlatform,
                              include_lazy = false,
                              pkg_uuid = nothing)
```

Retourne un dictionnaire où chaque entrée est un artefact du `Artifacts.toml` donné qui doit être téléchargé pour la plateforme demandée. Les artefacts paresseux sont inclus si `include_lazy` est défini.
