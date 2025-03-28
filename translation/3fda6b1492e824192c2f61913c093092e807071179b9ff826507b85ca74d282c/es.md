```
artifact_path(hash::SHA1; honor_overrides::Bool=true)
```

Dado un artefacto (identificado por el hash del árbol git SHA1), devuelve su ruta de instalación. Si el artefacto no existe, devuelve la ubicación a la que se instalaría.

!!! compat "Julia 1.3"
    Esta función requiere al menos Julia 1.3.

