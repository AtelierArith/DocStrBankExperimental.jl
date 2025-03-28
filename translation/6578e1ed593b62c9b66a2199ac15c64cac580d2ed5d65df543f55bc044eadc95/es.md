```
artifact_exists(hash::SHA1; honor_overrides::Bool=true)
```

Devuelve si el artefacto dado (identificado por su hash de árbol git sha1) existe en el disco. Ten en cuenta que es posible que el artefacto dado exista en múltiples ubicaciones (por ejemplo, dentro de múltiples depósitos).

!!! compat "Julia 1.3"
    Esta función requiere al menos Julia 1.3.

