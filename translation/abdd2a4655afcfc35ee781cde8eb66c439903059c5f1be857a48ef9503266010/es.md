```
artifact_meta(name::String, artifacts_toml::String;
              platform::AbstractPlatform = HostPlatform(),
              pkg_uuid::Union{Base.UUID,Nothing}=nothing)
```

Obtiene metadatos sobre un artefacto dado (identificado por nombre) almacenado dentro del archivo `(Julia)Artifacts.toml` dado. Si el artefacto es específico de la plataforma, utiliza `platform` para elegir el mapeo más apropiado. Si no se encuentra ninguno, devuelve `nothing`.

!!! compat "Julia 1.3"
    Esta función requiere al menos Julia 1.3.

