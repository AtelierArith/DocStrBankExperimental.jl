```
artifact_meta(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform(),
              pkg_uuid::Union{Base.UUID,Nothing}=nothing)
```

Obtenez des métadonnées sur un artefact donné (identifié par son nom) stocké dans le fichier `(Julia)Artifacts.toml` donné. Si l'artefact est spécifique à une plateforme, utilisez `platform` pour choisir le mappage le plus approprié. Si aucun n'est trouvé, renvoyez `nothing`.

!!! compat "Julia 1.3"
    Cette fonction nécessite au moins Julia 1.3.

