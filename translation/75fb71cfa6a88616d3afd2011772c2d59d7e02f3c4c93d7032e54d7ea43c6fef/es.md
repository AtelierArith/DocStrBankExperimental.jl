```
select_downloadable_artifacts(artifacts_toml::String;
                              platform = HostPlatform,
                              include_lazy = false,
                              pkg_uuid = nothing)
```

Devuelve un diccionario donde cada entrada es un artefacto del `Artifacts.toml` dado que debe ser descargado para la plataforma solicitada. Los artefactos perezosos se incluyen si `include_lazy` está configurado.
