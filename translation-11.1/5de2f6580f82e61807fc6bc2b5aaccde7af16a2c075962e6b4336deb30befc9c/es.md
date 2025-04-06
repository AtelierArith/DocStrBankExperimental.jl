```
pathof(m::Module)
```

Devuelve la ruta del archivo `m.jl` que se utilizó para `importar` el módulo `m`, o `nada` si `m` no fue importado de un paquete.

Utiliza [`dirname`](@ref) para obtener la parte del directorio y [`basename`](@ref) para obtener la parte del nombre del archivo de la ruta.

Ver también [`pkgdir`](@ref).
