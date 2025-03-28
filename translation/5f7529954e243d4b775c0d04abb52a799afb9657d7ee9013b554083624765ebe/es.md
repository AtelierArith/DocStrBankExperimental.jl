```
artifact_hash(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform())
```

Envoltura delgada alrededor de `artifact_meta()` para devolver el hash del artefacto colapsado especificado para la plataforma. Devuelve `nothing` si no se puede encontrar un mapeo.

!!! compat "Julia 1.3"
    Esta función requiere al menos Julia 1.3.

