```
select_downloadable_artifacts(artifacts_toml::String;
                              platform = HostPlatform,
                              include_lazy = false,
                              pkg_uuid = nothing)
```

Gibt ein Wörterbuch zurück, in dem jeder Eintrag ein Artefakt aus der angegebenen `Artifacts.toml` ist, das für die angeforderte Plattform heruntergeladen werden soll. Lazy-Artefakte werden einbezogen, wenn `include_lazy` auf true gesetzt ist.
