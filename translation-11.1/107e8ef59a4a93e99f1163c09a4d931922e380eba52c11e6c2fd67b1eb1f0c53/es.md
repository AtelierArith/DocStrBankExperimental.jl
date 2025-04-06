```
pkgversion(m::Module)
```

Devuelve la versión del paquete que importó el módulo `m`, o `nothing` si `m` no fue importado de un paquete, o importado de un paquete sin un campo de versión establecido.

La versión se lee del Project.toml del paquete durante la carga del paquete.

Para obtener la versión del paquete que importó el módulo actual, se puede usar la forma `pkgversion(@__MODULE__)`.

!!! compat "Julia 1.9"
    Esta función fue introducida en Julia 1.9.

