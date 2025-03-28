```
find_artifacts_toml(path::String)
```

Dado el camino a un archivo `.jl` (como el que se devuelve por `__source__.file` en un contexto de macro), encuentra el `(Julia)Artifacts.toml` que está contenido dentro del proyecto contenedor (si existe), de lo contrario devuelve `nothing`.

!!! compat "Julia 1.3"
    Esta función requiere al menos Julia 1.3.

