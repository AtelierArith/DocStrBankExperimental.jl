```
artifact_hash(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform())
```

Enveloppe fine autour de `artifact_meta()` pour retourner le hachage de l'artefact spécifié, réduit par la plateforme. Retourne `nothing` si aucun mappage ne peut être trouvé.

!!! compat "Julia 1.3"
    Cette fonction nécessite au moins Julia 1.3.

