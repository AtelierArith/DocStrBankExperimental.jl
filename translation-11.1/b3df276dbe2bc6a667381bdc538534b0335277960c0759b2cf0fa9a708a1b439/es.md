```
Base.isprecompiled(pkg::PkgId; ignore_loaded::Bool=false)
```

Devuelve si un PkgId dado dentro del proyecto activo está precompilado.

Por defecto, esta verificación observa el mismo enfoque que la carga de código con respecto a cuándo se cargan diferentes versiones de las dependencias en comparación con lo que se espera. Para ignorar los módulos cargados y responder como si estuvieras en una nueva sesión de julia, especifica `ignore_loaded=true`.

!!! compat "Julia 1.10"
    Esta función requiere al menos Julia 1.10.

