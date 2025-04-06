```
artifact_hash(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform())
```

Dünne Wrapper um `artifact_meta()`, um den Hash des angegebenen, plattform-kollabierten Artefakts zurückzugeben. Gibt `nothing` zurück, wenn keine Zuordnung gefunden werden kann.

!!! compat "Julia 1.3"
    Diese Funktion erfordert mindestens Julia 1.3.

