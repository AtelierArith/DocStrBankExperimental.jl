```
artifact_meta(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform(),
              pkg_uuid::Union{Base.UUID,Nothing}=nothing)
```

Holen Sie sich Metadaten über ein gegebenes Artefakt (identifiziert durch den Namen), das in der gegebenen `(Julia)Artifacts.toml`-Datei gespeichert ist. Wenn das Artefakt plattformspezifisch ist, verwenden Sie `platform`, um die am besten geeignete Zuordnung auszuwählen. Wenn keine gefunden wird, geben Sie `nothing` zurück.

!!! compat "Julia 1.3"
    Diese Funktion erfordert mindestens Julia 1.3.

