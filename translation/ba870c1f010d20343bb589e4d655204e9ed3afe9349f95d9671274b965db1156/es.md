```
basename(path::AbstractString) -> String
```

Obtiene la parte del nombre del archivo de una ruta.

!!! note
    Esta función difiere ligeramente del programa `basename` de Unix, donde las barras finales se ignoran, es decir, `$ basename /foo/bar/` devuelve `bar`, mientras que `basename` en Julia devuelve una cadena vacía `""`.


# Ejemplos

```jldoctest
julia> basename("/home/myuser/example.jl")
"example.jl"

julia> basename("/home/myuser/")
""
```

Ver también [`dirname`](@ref).
