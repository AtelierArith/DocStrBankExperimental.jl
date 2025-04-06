```
pkgdir(m::Module[, paths::String...])
```

Devuelve el directorio raíz del paquete que declaró el módulo `m`, o `nothing` si `m` no fue declarado en un paquete. Opcionalmente, se pueden proporcionar cadenas de componentes de ruta adicionales para construir una ruta dentro del directorio raíz del paquete.

Para obtener el directorio raíz del paquete que implementa el módulo actual, se puede usar la forma `pkgdir(@__MODULE__)`.

Si se proporciona un módulo de extensión, se devuelve la raíz del paquete padre.

```julia-repl
julia> pkgdir(Foo)
"/path/to/Foo.jl"

julia> pkgdir(Foo, "src", "file.jl")
"/path/to/Foo.jl/src/file.jl"
```

Ver también [`pathof`](@ref).

!!! compat "Julia 1.7"
    El argumento opcional `paths` requiere al menos Julia 1.7.

